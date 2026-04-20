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
            }
class Phoenix_to_MyGCPay {
+Pay_stub_details
+Deductions
+Tax_slips
+Pay_history
+Case_&_Enquiry_Status
+Direct_deposit_info
            }
}
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
 class MyGCHR_to_MyGCPay {
+Leave_balances
+Work_schedule
+Job_&_employment_records
+Benefits_service_date
+Personal_profile_data
            }

TRST --> MyGCHR: SLE results
SIGMA --> MyGCHR: Financial delegation
MyGCHR --> Phoenix: real time integration
MyHRRP --> MyGCHR: RPA
MyHRRP --> MyGCHR: Manual entry
MyGCHR --> HRSD
MyGCHR --> MyGCHR_to_MyGCPay: HR-specific info
MyGCHR_to_MyGCPay --> MyGCPay: HR-specific info
Phoenix_to_MyGCPay --> MyGCPay: financial and case status data
Phoenix  --> Phoenix_to_MyGCPay
HRSD --> MyGCHR: Manual entry
Phoenix --> CRA: Taxes
Phoenix --> Canada_Post: T4, R1, etc.
Phoenix --> Unions: Deductions
Phoenix --> Banks: Deductions
Phoenix --> Insurances_compagnies: Contributions
Phoenix --> Service_Canada: Renumeration records
Phoenix --> Provincial_Revenue: Renumeration records
