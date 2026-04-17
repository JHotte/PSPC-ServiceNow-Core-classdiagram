```mermaid
classDiagram
direction LR
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
            }
    }
TRST --> MyGCHR: SLE results
SIGMA --> MyGCHR: Financial delegation
MyGCHR --> Phoenix
