```mermaid
classDiagram
namespace TBS {
class Open_Canada_Dataset {
Portal open.canada.ca
}
class Concordance_data {
Name: GoC Org. Names and Codes - Concordance Data
+key: gc_orgID
}
class Organization_information {
Name: GoC Org. Names and Codes - Organization Information
+key: gc_orgID
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
     class sys_user {
User Profiles
Status: active
}
class cmn_location {
Location
Status: active
}
class business_unit {
PSPC Branches (L1)
}
}
%% links %%
Open_Canada_Dataset -- Organization_information: host
Open_Canada_Dataset -- Concordance_data : host
Organization_information -- customer_account: weekly feed
Concordance_data -- customer_account: weekly feed
customer_account -- core_company: extends
core_company -- business_unit: "company"
core_company -- sys_user: "company"
core_company -- cmn_location: "company"
