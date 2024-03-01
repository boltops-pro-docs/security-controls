<!-- note marker start -->
NOTE: This repo contains only the documentation for the private BoltsOps repo code.
Original file: https://github.com/boltops-pro/security-controls/blob/master/app/files/lambda/vendor/s3-secure/CHANGELOG.md
The docs are publish so they are available for interested subscribers.
For access to the source code, you can become a BoltOps subscriber.
See: https://learn.boltops.com

<!-- note marker end -->

# Change Log

All notable changes to this project will be documented in this file.
This project *tries* to adhere to [Semantic Versioning](http://semver.org/), even before v1.0.

## [0.1.0]
- add commands: access_logs, lifecycle, versioning, remediate_all
- community version only has: encryption and policy
- s3 client is smarter and switches regions on a per-bucket basis

# Original Community Version Changelog

## [0.4.2]
- improve error message for Aws::STS::Errors::RegionDisabledException error

## [0.4.1]
- improve cli help

## [0.4.0]
-  #1 summary command

## [0.3.0]
- clean up policy_document method interface

## [0.2.0]
- encryption enable: add kms-key option

## [0.1.0]
- Initial release.
