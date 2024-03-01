<!-- note marker start -->
NOTE: This repo contains only the documentation for the private BoltsOps repo code.
Original file: https://github.com/boltops-pro/security-controls/blob/master/app/files/lambda/vendor/security-group/README.md
The docs are publish so they are available for interested subscribers.
For access to the source code, you can become a BoltOps subscriber.
See: https://learn.boltops.com

<!-- note marker end -->

# security-group CLI tool and library

[![BoltOps Badge](https://img.boltops.com/boltops/badges/boltops-badge.png)](https://www.boltops.com)

The security-group tool can be used to harden your security group posture. It provides a command to close security group ports 22 (SSH) and 3389 (RDP) that have been opened to the world, 0.0.0.0/0.

It is used as part of these blueprints:

* [Security Group Closer](https://github.com/boltopspro/security-group-closer): Watches for changes in security group rules via CloudWatch Events and automatically closes the port. It'll also send an SNS topic notification telling you who opened it.
* [Security Controls](https://github.com/boltopspro/security-controls): Continuously applies the security-group remedation as well as other remeidations. IE: S3 Buckets, SNS topics, etc.

## Usage

    security-group close SECURITY_GROUP_ID
    security-group close sg-111

## Installation

Install with:

    git clone git@github.com:boltopspro/security-group
    bundle
    rake install
