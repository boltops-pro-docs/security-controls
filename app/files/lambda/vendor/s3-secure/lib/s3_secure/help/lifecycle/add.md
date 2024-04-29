<!-- note marker start -->
NOTE: This repo contains only the documentation for the private BoltsOps repo code.
Original file: https://github.com/boltops-pro/security-controls/blob/master/app/files/lambda/vendor/s3-secure/lib/s3_secure/help/lifecycle/add.md
The docs are publish so they are available for interested subscribers.
For access to the source code, you can become a BoltOps subscriber.
See: https://learn.boltops.com

<!-- note marker end -->

## Example

    $ s3-secure lifecycle add a-test-bucket-in-us-east-1
    Added lifecycle policy to bucket a-test-bucket-in-us-east-1
    $

By default, the add command will only add a lifecycle policy if you none exists.

It may be useful to test adding an additional lifecycle policy, for this you can use both the `--additive` and `--prefix` options. Note, you must make sure that the lifecycle policies can work together. For example, they must have different prefixes.

    $ s3-secure lifecycle add a-test-bucket-in-us-east-1 --additive --prefix /foo
    Added lifecycle policy to bucket a-test-bucket-in-us-east-1
    $