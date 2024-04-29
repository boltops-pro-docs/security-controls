<!-- note marker start -->
NOTE: This repo contains only the documentation for the private BoltsOps repo code.
Original file: https://github.com/boltops-pro/security-controls/blob/master/app/files/lambda/vendor/sns-secure/lib/sns_secure/help/completion.md
The docs are publish so they are available for interested subscribers.
For access to the source code, you can become a BoltOps subscriber.
See: https://learn.boltops.com

<!-- note marker end -->

## Examples

    sns-secure completion

Prints words for TAB auto-completion.

    sns-secure completion
    sns-secure completion hello
    sns-secure completion hello name

To enable, TAB auto-completion add the following to your profile:

    eval $(sns-secure completion_script)

Auto-completion example usage:

    sns-secure [TAB]
    sns-secure hello [TAB]
    sns-secure hello name [TAB]
    sns-secure hello name --[TAB]
