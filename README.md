<!-- note marker start -->
**NOTE**: This repo contains only the documentation for the private BoltsOps Pro repo code.
Original file: https://github.com/boltopspro/security-controls/blob/master/README.md
The docs are publish so they are available for interested customers.
For access to the source code, you must be a paying BoltOps Pro subscriber.
If are interested, you can contact us at contact@boltops.com or https://www.boltops.com

<!-- note marker end -->

# Security Controls Blueprint

[![BoltOps Badge](https://img.boltops.com/boltops/badges/boltops-badge.png)](https://www.boltops.com)

This blueprint provisions several [Lambda Functions](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-lambda-function.html) to apply security controls continuously on your AWS resources for compliance. It can be use as-is. It can also serve as an example to be forked if the controls do not perfectly fit your requirements.  The current controls:

* s3 bucket hardening: automatically enable access logs, encryption, lifecycle policy, ensure ssl bucket policy.
* security groups: automatically close port 22 (SSH) and 3389 (RD) if they are opened to the world. Sends SNS topic notification telling you who opened the port.
* sns topic encryption: automatically enables encryption on SNS Topics.

By design, the automatic controls apply to new AWS resources on a go-forward based only. This removes the risk of disrupting current running services. To retroactively remediate existing resources quickly, you can use the companion tools:

* [s3-secure-cli](https://github.com/boltopspro-docs/s3-secure-cli)
* [security-group-cli](https://github.com/boltopspro-docs/security-group-cli)
* [sns-secure-cli](https://github.com/boltopspro-docs/sns-secure-cli)

## Usage

1. Add blueprint to Gemfile
2. Configure: configs/security-controls values
3. Deploy blueprint

## Add

Add the blueprint to your lono project's `Gemfile`.

```ruby
gem "security-controls", git: "git@github.com:boltopspro/security-controls.git", submodules: true
```

## Configure

Use the [lono seed](https://lono.cloud/reference/lono-seed/) command to generate a starter config params files.

    LONO_ENV=development lono seed security-controls
    LONO_ENV=production  lono seed security-controls

The files in `config/security-controls` folder will look something like this:

    configs/security-controls/
    └── variables
        ├── development.rb
        └── production.rb

Configure the `configs/security-controls/variables` files.

## Deploy

Use the [lono cfn deploy](http://lono.cloud/reference/lono-cfn-deploy/) command to deploy.

    LONO_ENV=development lono cfn deploy security-controls --sure --no-wait
    LONO_ENV=production  lono cfn deploy security-controls --sure --no-wait

If you are using One AWS Account, use these commands instead: [One Account](docs/one-account.md).


### Adding Additional Controls

To add additional controls, follow these steps:

1. Add control method [app/templates/controls_helper.rb](app/templates/controls_helper.rb)
2. Call method in [app/templates/security-controls.rb](app/templates/security-controls.rb)
3. Define corresponding class in [app/files/lambda/lib/secure/control] - The other classes provide examples and shows the interface to implement. Simply the `run` method is required.

### Lambda Function in VPC

To configure the Lambda function with VpcConfig set `@subnet_ids` and either `@vpc_id` or `@security_group_ids`.

* When the `@vpc_id` is set, the template creates a managed security group for you and the Lambda function is configured to use that security group.
* When `@security_group_ids` is set, the Lambda function will use those existing security groups.
* The subnet must be a private subnet with configured with a NAT.

Here's an example of the managed security group.

configs/security-controls/variables/development.rb:

```ruby
@subnet_ids = ["subnet-111"]
@vpc_id = "vpc-111"
```

For Lambda VPC to work, the subnet must be a private subnet configured with a NAT. The security group must also allow access. Here's an example that opens all ports for the VPC CIDR range:

```ruby
@security_group_ingress = [{
  CidrIp: stack_output("vpc.VpcCidr"),
  IpProtocol: -1,
}]
```

Note, Lambda functions configured with VPCs may take much longer to deploy, typically 30-45 minutes. This is because Lambda creates and attaches an ENI to the Lambda function to make the VPC feature possible. If the function is deleted or updated, requiring replacement, the ENI takes 30-45m to be removed. Because of this, it is recommended to write code for your Lambda function code without the VpcConfig first. Get it working and then add VpcConfig at the end.

### X-Ray Tracing

Lambda X-Ray tracing is set to `Active` by default. You can disable this by setting `@tracing_config_mode = false`. Example:

configs/security-controls/variables/development.rb:

```ruby
@tracing_config_mode = false
```

You can also change the mode with the same `@tracing_config_mode` variable:

```ruby
@tracing_config_mode = "Active" # or "PassThrough"
```
