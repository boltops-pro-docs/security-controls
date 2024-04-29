<!-- note marker start -->
NOTE: This repo contains only the documentation for the private BoltsOps repo code.
Original file: https://github.com/boltops-pro/security-controls/blob/master/app/files/lambda/vendor/s3-secure/lib/s3_secure/help/completion.md
The docs are publish so they are available for interested subscribers.
For access to the source code, you can become a BoltOps subscriber.
See: https://learn.boltops.com

<!-- note marker end -->

## Examples

    s3-secure completion

Prints words for TAB auto-completion.

    s3-secure completion
    s3-secure completion hello
    s3-secure completion hello name

To enable, TAB auto-completion add the following to your profile:

    eval $(s3-secure completion_script)

Auto-completion example usage:

    s3-secure [TAB]
    s3-secure hello [TAB]
    s3-secure hello name [TAB]
    s3-secure hello name --[TAB]
