<!-- note marker start -->
NOTE: This repo contains only the documentation for the private BoltsOps repo code.
Original file: https://github.com/boltops-pro/security-controls/blob/master/app/files/lambda/vendor/s3-secure/lib/s3_secure/help/summary.md
The docs are publish so they are available for interested subscribers.
For access to the source code, you can become a BoltOps subscriber.
See: https://learn.boltops.com

<!-- note marker end -->

## Examples

    $ s3-secure summary
    Determining bucket security-related settings...
    +----------------------------+------+------------+
    |           Bucket           | SSL? | Encrypted? |
    +----------------------------+------+------------+
    | a-test-bucket-in-us-east-1 | yes  | no         |
    | a-test-bucket-in-us-west-1 | no   | no         |
    +----------------------------+------+------------+
    $

There are `--ssl no` and `--encrypted no` filtering options:

    $ s3-secure summary --ssl no --encrypted no
    Determining bucket security-related settings...
    +----------------------------+------+------------+
    |           Bucket           | SSL? | Encrypted? |
    +----------------------------+------+------------+
    | a-test-bucket-in-us-west-1 | no   | no         |
    +----------------------------+------+------------+
    $