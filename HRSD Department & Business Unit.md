

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
class Business Unit {
Name: business_unit
}
class Department {
Name: cmn_department
}
class Cost Center {
Name: cmn_cost_center
}
class HR Integrations Source
class Integration Source
class Company
class User
}
AD -- PSPCD
Department -- Business Unit
Department .. Cost Center : unused
Department .. HR Integrations Source : unused
Department .. Integration Source : unused
Department .. Company : unused
Department .. User : unused
Business Unit .. User : unused
Business Unit .. Company : unused
