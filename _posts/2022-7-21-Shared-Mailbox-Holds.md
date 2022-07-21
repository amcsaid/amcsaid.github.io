---
layout: post
title: Shared Mailboxes and Hold situations
---

To access the logs for mailboxes, it is possible using  2 methods:

-   **Compliance Center > Audit**
    -   This might be limited as it returns actions done by the Users on all Mailboxes including the shared ones. (For results unique to Shared Mailboxes, in a previous ticket you opened with us we already escalated this to Microsoft about having this option and it requires a license.)
    -   Alternatively, as we explained, you can use the following Powershell command to get the same results from the Unified Audit Log and customize the output (or create a PS script) to fit your current business needs:  **Search-UnifiedAuditLog**, further documentation can be obtained at [Search-UnifiedAuditLog (ExchangePowerShell) | Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/exchange/search-unifiedauditlog?view=exchange-ps)
-   **Exchange Classic Admin Center > Compliance Management > Auditing**
    -   On this portal, you can access logs instantly or opt out to receive the logs as report via email. More details about the auditing options available here: [Auditing reports in the Exchange admin center in Exchange Online | Microsoft Docs](https://docs.microsoft.com/en-us/exchange/security-and-compliance/exchange-auditing-reports/exchange-auditing-reports)
    -   This will eventually be deprecated, according to Microsoft, on September 2022 (Source: [Deprecation of the classic Exchange admin center in WW service - Microsoft Tech Community](https://techcommunity.microsoft.com/t5/exchange-team-blog/deprecation-of-the-classic-exchange-admin-center-in-ww-service/ba-p/2736358))
    -   Alternatively, this command **Search-MailboxAuditLog** can give you similar results to the reports obtained via Classic EAC. Again, you can customize it to fit your needs by exploring your options here: [Search-MailboxAuditLog (ExchangePowerShell) | Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/exchange/search-mailboxauditlog?view=exchange-ps)
        -   For example:
            -   Search-MailboxAuditLog  _[mailbox@domain.com](mailto:mailbox@domain.com)_ -ShowDetails -ResultSize _5_  | ft Operation, LogonType, LogonUserDisplayName, ItemSubject
            -   This should return the most recent 5 operations done on a mailbox by users with delegated access, the output will have the operation type, logon type, logged user, and the message subject.
    -   Another command which has the same functionality, the report emailed to you on EAC is the **New-MailboxAuditLogSearch,** again this can be used to fit your needs, please check:  [New-MailboxAuditLogSearch (ExchangePowerShell) | Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/exchange/new-mailboxauditlogsearch?view=exchange-ps)
