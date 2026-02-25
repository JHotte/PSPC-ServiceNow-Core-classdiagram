```mermaid
classDiagram
%% TBS
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
%% PSPC
namespace PSPC {
class AD {
Active Directory
}
class PSPCD {
PSPC Directory
}
}
%% ServiceNow
namespace ServiceNow {
class business_unit {
Business Unit
}
class cmn_department {
Department
}
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
customer_account -- sys_user : "contact"
core_company -- sys_user : "contact"
cmn_location -- core_company: "company"
AD -- PSPCD
cmn_department -- business_unit : "Business Unit"
cmn_department -- core_company : "Company"
cmn_department -- sys_user : "Department Head, Primary Contact''
business_unit -- core_company : "Company"
PSPCD -- business_unit : refered
PSPCD -- cmn_department : refered

business_unit -- sys_user : "Business Unit Head"



