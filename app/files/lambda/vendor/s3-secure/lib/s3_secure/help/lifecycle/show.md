<!-- note marker start -->
NOTE: This repo contains only the documentation for the private BoltsOps repo code.
Original file: https://github.com/boltops-pro/security-controls/blob/master/app/files/lambda/vendor/s3-secure/lib/s3_secure/help/lifecycle/show.md
The docs are publish so they are available for interested subscribers.
For access to the source code, you can become a BoltOps subscriber.
See: https://learn.boltops.com

<!-- note marker end -->

## Examples

    $ s3-secure lifecycle show a-test-bucket-in-us-east-1
    This S3 bucket has lifecycle rules
    Bucket lifecycle details:
    {:rules=>
      [{:expiration=>{:expired_object_delete_marker=>true},
        :id=>"s3-secure-automated-cleanup",
        :prefix=>"/bar",
        :status=>"Enabled",
        :noncurrent_version_expiration=>{:noncurrent_days=>365},
        :abort_incomplete_multipart_upload=>{:days_after_initiation=>30}}]}
    $