

```mermaid
%% TBS   
classDiagram
namespace PSPC {
class AD {
Name: Active Directory
}
class PSPCD {
Name: PSPC Directory
}
}
namespace ServiceNow {
class business_unit {
Business Unit
}
class cmn_department {
Department
}
class core_company {
Company
}
class sys_user
}
AD -- PSPCD
cmn_department -- business_unit : "Business Unit"
cmn_department -- core_company : "Company"
cmn_department -- sys_user : "Department Head, Primary Contact''
business_unit -- sys_user : "Business Unit Head"
business_unit -- core_company : "Company"
PSPCD -- business_unit : refered
PSPCD -- cmn_department : refered
