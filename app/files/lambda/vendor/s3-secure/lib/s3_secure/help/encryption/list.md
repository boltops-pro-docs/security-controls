<!-- note marker start -->
NOTE: This repo contains only the documentation for the private BoltsOps repo code.
Original file: https://github.com/boltops-pro/security-controls/blob/master/app/files/lambda/vendor/s3-secure/lib/s3_secure/help/encryption/list.md
The docs are publish so they are available for interested subscribers.
For access to the source code, you can become a BoltOps subscriber.
See: https://learn.boltops.com

<!-- note marker end -->

## Examples

    s3-secure encryption list                 # shows all buckets with and without polices
    s3-secure encryption list --encryption    # only shows buckets with encryption
    s3-secure encryption list --no-encryption # only shows buckets without encryption
