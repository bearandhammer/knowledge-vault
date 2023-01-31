
1. We can use a more robust oauth flow, with the more broad 'application permissions' enabled but with an `ApplicationAccessPolicy` in place to limit the mailboxes typical users can generally access:

***There are scenarios where administrators may want to limit an app to only specific mailboxes and _not all_ Exchange Online mailboxes in the organization. Administrators can identify the set of mailboxes to permit access by putting them in a mail-enabled security group. Administrators can then limit third-party app access to only that set of mailboxes by creating an application access policy for access to that group.***

https://learn.microsoft.com/en-us/graph/auth-limit-mailbox-access

So we could do something like (requires testing): https://www.cloudappie.nl/limit-app-permissions-specific-mailbox/

2. We can use a more legacy oauth flow for now - continuing to provide the password (encrypt) along with the app id/secret. This approach is deprecated, but still functionally in oauth 2 (removed in oauth 2.1).

