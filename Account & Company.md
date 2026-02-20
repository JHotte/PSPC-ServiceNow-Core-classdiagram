

```mermaid
%% TBS   
classDiagram
class Treasury_Board_Secretariat {
}
class Open_Canada_Dataset {
}
Open_Canada_Dataset -- Treasury_Board_Secretariat : owner
class Concordance_Data {
Name: Government of Canada Organization Names and Codes - Concordance Data
}
Concordance_data -- Account
Concordance_data -- Company
Open_Canada_Dataset -- Concordance_Data : host
class Organization_information {
Name: Government of Canada Organization Names and Codes - Organization Information
}
Organization_information -- Account
Organization_information -- Company
Open_Canada_Dataset -- Organization_information : host
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
