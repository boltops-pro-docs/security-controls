<!-- note marker start -->
NOTE: This repo contains only the documentation for the private BoltsOps repo code.
Original file: https://github.com/boltops-pro/security-controls/blob/master/app/files/lambda/vendor/s3-secure/lib/s3_secure/help/policy/enforce_ssl.md
The docs are publish so they are available for interested subscribers.
For access to the source code, you can become a BoltOps subscriber.
See: https://learn.boltops.com

<!-- note marker end -->

## Example

    $ s3-secure policy enforce_ssl a-test-bucket-in-us-east-1
    Add bucket policy to bucket a-test-bucket-in-us-east-1:
    {
      "Version": "2012-10-17",
      "Statement": [
        {
          "Sid": "IPAllow",
          "Effect": "Deny",
          "Principal": "*",
          "Action": "s3:*",
          "Resource": "arn:aws:s3:::a-test-bucket-in-us-east-1/*",
          "Condition": {
            "NotIpAddress": {
              "aws:SourceIp": "54.240.143.0/24"
            }
          }
        },
        {
          "Sid": "ForceSSLOnlyAccess",
          "Effect": "Deny",
          "Principal": "*",
          "Action": "s3:GetObject",
          "Resource": "arn:aws:s3:::a-test-bucket-in-us-east-1/*",
          "Condition": {
            "Bool": {
              "aws:SecureTransport": "false"
            }
          }
        }
      ]
    }
    $