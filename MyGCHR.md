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
+Employment_data(HR_Profile)
+Position_data(positions)
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
class MyGCHR_to_HRSD {
+Locations

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
 class MyGCHR_to_MyGCPay {
+Leave_balances
+Work_schedule
+Job_&_employment_records
+Benefits_service_date
+Personal_profile_data
            }
 class 3rd_party {
+Insurances_compagnies(coverages)
+Banks(direct_deposit)
+Unions(memberships)
+CRA(taxes)
+Canada_post(T4,R1,etc.)
+Service_Canada(remuneration_records)
+Provilcial_revenue(remuneration_records)
            }
namespace ServiceNow {
    class MID_Server {
+HR_Profile_data
            }}
TRST --> MyGCHR: SLE results
SIGMA --> MyGCHR: Financial delegation
MyGCHR --> Phoenix: real time integration
MyGCHR --> MID_Server
MyGCHR --> MyGCHR_to_HRSD : manual upload
MyGCHR_to_HRSD --> HRSD
MID_Server -->  HRSD
MyHRRP --> MyGCHR: RPA
MyHRRP --> MyGCHR: manual entry
MyGCHR --> MyGCHR_to_MyGCPay: HR-specific info
MyGCHR_to_MyGCPay --> MyGCPay: HR-specific info
Phoenix_to_MyGCPay --> MyGCPay: financial and case status data
Phoenix  --> Phoenix_to_MyGCPay
Phoenix  --> 3rd_party
HRSD --> MyGCHR: manual entry
