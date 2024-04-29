<!-- note marker start -->
NOTE: This repo contains only the documentation for the private BoltsOps repo code.
Original file: https://github.com/boltops-pro/security-controls/blob/master/app/files/lambda/vendor/s3-secure/lib/s3_secure/help/lifecycle/list.md
The docs are publish so they are available for interested subscribers.
For access to the source code, you can become a BoltOps subscriber.
See: https://learn.boltops.com

<!-- note marker end -->

## Examples

    $ s3-secure lifecycle list
    +----------------------------+----------------------+
    |           Bucket           | Has Lifecycle Rules? |
    +----------------------------+----------------------+
    | a-test-bucket-in-us-east-1 | false                |
    | a-test-bucket-in-us-west-1 | true                 |
    +----------------------------+----------------------+
    $ s3-secure lifecycle list --lifecycle true
    +----------------------------+----------------------+
    |           Bucket           | Has Lifecycle Rules? |
    +----------------------------+----------------------+
    | a-test-bucket-in-us-west-1 | true                 |
    +----------------------------+----------------------+
    $ s3-secure lifecycle list --lifecycle false
    +----------------------------+----------------------+
    |           Bucket           | Has Lifecycle Rules? |
    +----------------------------+----------------------+
    | a-test-bucket-in-us-east-1 | false                |
    +----------------------------+----------------------+
    $