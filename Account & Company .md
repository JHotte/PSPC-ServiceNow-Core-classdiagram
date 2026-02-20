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
Status: active
Content: FAA schedule, abbreviations, etc()
}
    class Company {
Name: core_company
Status: active
Content: Full names, accronym, hierarchy structure()
}
    class Contact {
Name: customer_contact
Status: inactive
}
    class User {
Name: sys_user
Status: active
}
    class Theme {
Name: sys_ui_theme
Status: inactive
    }
 class Escalation {
Name: sn_customerservice_escalation
Status: inactive
    }
class task {
}
}
Open_Canada_Dataset -- Concordance_data : host
Open_Canada_Dataset -- Organization_information : host
Concordance_data -- Account : refered
Organization_information -- Account : refered
Account -- Company : extend
Account .. Contact : unused
Account .. User : unused
Account .. Escalation : unused
Account .. Theme : unused
Company .. User : unused
Company .. Theme : unused
Contact -- User : extend
Escalation -- task : extend
