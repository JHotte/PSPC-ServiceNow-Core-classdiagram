

```mermaid
%% TBS   
classDiagram
    class Account {
ServiceNow
Name: customer_account
    }
    class Company {
ServiceNow
Name: core_company
    }
Account <|-- Company : Extend
User .. Company : Unused
    class Contact {
ServiceNow
Name: customer_contact
    }
Account .. Contact: unused
    class User {
ServiceNow
Name: sys_user
    }
Account .. User: unused
User .. Company: unused
    class Escalation {
ServiceNow
Name: sn_customerservice_escalation
    }
Account .. Escalation: unused
    class Theme {
ServiceNow
Name: sys_ui_theme
    }
Account .. Theme: unused
