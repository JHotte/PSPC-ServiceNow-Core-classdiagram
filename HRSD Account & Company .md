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
    class customer_account {
Account
Status: active
Content: FAA schedule, abbreviations, etc()
}
    class core_company {
Company
Status: active
Content: Full names, accronym, hierarchy structure()
}
    class customer_contact {
Contact
Status: inactive
}
    class sys_user {
User Profiles
Status: active
}
class cmn_location {
Location
Status: active
}
}
Open_Canada_Dataset -- Concordance_data : host
Open_Canada_Dataset -- Organization_information : host
Concordance_data -- customer_account : refered
Concordance_data -- core_company : refered
Organization_information -- customer_account : refered
Organization_information -- core_company : refered
customer_account --> core_company : parent
customer_account .. customer_contact : "contact"
customer_account .. sys_user : "contact"
core_company .. sys_user : "contact"
customer_contact -- sys_user : "manager"
cmn_location -- core_company: "company"
