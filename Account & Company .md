```mermaid
classDiagram
namespace TBS {
class Open_Canada_Dataset {
}
class Concordance_data {
Name: GoC Org. Names and Codes - Concordance Data
}
class Organization_information {
Name: GoC Org. Names and Codes - Organization Information
}
}
namespace ServiceNow {
    class Account {
Name: customer_account
}
    class Company {
Name: core_company
}
    class Contact {
Name: customer_contact
}
    class User {
Name: sys_user
}
    class Theme {
Name: sys_ui_theme
    }
 class Escalation {
Name: sn_customerservice_escalation
    }
}
Open_Canada_Dataset -- Concordance_data : host
Open_Canada_Dataset -- Organization_information : host
Account -- Company : extend
Account -- Contact
Account -- User
Account -- Escalation
Account -- Theme
Company -- User
Company -- Theme
