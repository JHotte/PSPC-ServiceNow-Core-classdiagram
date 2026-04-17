```mermaid
classDiagram
namespace Public_Service_Commission {
    class TRST {
+SLE_results
            } }
namespace Human_Resources {
    class MyGCHR {
+employee_profile
+position_profile
            }
class MyHRRP {
+MyGCHR_support
+HR_requests_and_supports
+Express_staffing
+Operational_staffing
+Collective_staffing
+Administrative_changes
+LWP/LWOP/RFL
+Employee_PAR
+Manager_PAR
+HR_pros
+HRB_inquiries
+SLE_testing_queue
            }
class HRSD {
+Conflict_of_Interest
+Pay_benefits_pension
+Departure_early_end
            } 
}
namespace Finances {
    class SIGMA {
+financial_delegation
            } }
namespace Human_Capital_Management {
    class Phoenix {
            }
    class MyGCPay {
            }}
namespace RGPB {
 class Penfax {
            }
    }
    namespace 3rd_parties_system {
 class CRA {
+taxes
            }
 class Canada_Post {
            }
 class Unions {
+memberships
            }
 class Banks {
+direct_deposit
            }
 class Insurances_compagnies {
+coverages
            }
 class Service_Canada {
            }
 class Provincial_Revenue {
            }
    }
TRST --> MyGCHR: SLE results
SIGMA --> MyGCHR: Financial delegation
MyGCHR --> Phoenix
MyHRRP --> MyGCHR: RPA
MyHRRP --> MyGCHR: Manual entry
MyGCHR --> HRSD
MyGCHR --> MyGCPay
HRSD --> MyGCHR: Manual entry
Phoenix --> CRA: Taxes
Phoenix --> Canada_Post: T4, R1, etc.
Phoenix --> Unions: Deductions
Phoenix --> Banks: Deductions
Phoenix --> Insurances_compagnies: Contributions
Phoenix --> Service_Canada: Renumeration records
Phoenix --> Provincial_Revenue: Renumeration records
