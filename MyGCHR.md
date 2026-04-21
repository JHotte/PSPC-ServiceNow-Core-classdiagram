```mermaid
classDiagram
direction LR
namespace Public_Service_Commission {
    class TRST {
        +SLE_results
    }
}
namespace Human_Resources {
    class MyGCHR {
        +employee_profile
        +position_profile
        +Employment_data
        +Position_data
    }
    class MyHRRP {
        +MyGCHR_support
        +HR_requests_and_supports
        +Express_staffing
        +Operational_staffing
        +Administrative_changes
        +LWP_LWOP_RFL
        +Employee_PAR
        +Manager_PAR
        +HRB_inquiries
        +SLE_testing_queue
    }
    class MyGCHR_to_HRSD {
        +Locations
        +Positions
    }
}
namespace On_Premises_Infrastructure {
    class HRDataMart {
        +Oracle_DB
        +JDBC_source
        +Employment_data
    }
}
namespace Finances {
    class SIGMA {
        +financial_delegation
    }
}
namespace Human_Capital_Management {
    class Phoenix {
payroll_processing-system
    }
    class MyGCPay {
web_app
    }
    class Phoenix_to_MyGCPay {
        +Pay_stub_details
        +Deductions
        +Tax_slips
        +Pay_history
        +Case_and_Enquiry_Status
        +Direct_deposit_info
    }
}
namespace ServiceNow {
    class MID_Server {
        +MyGCHR
        +Exchange
        +AD
    }

    class HRSD {
        +Conflict_of_Interest
        +Pay_benefits_pension
        +Departure_early_end
    }
}
class MyGCHR_to_MyGCPay {
    +Leave_balances
    +Work_schedule
    +Job_and_employment_records
    +Benefits_service_date
    +Personal_profile_data
}
class Third_party {
    +Insurance_companies
    +Banks
    +Unions
    +CRA
    +Canada_Post
    +Service_Canada
    +Provincial_revenue
}
TRST --> MyGCHR : SLE results
SIGMA --> MyGCHR : Financial delegation
MyGCHR --> Phoenix : real time integration
MyGCHR --> HRDataMart : integration
HRDataMart --> MID_Server : JDBC
MID_Server --> HRSD : Transform map
MyGCHR --> MyGCHR_to_HRSD : manual upload
MyGCHR_to_HRSD --> HRSD : manual upload
MyHRRP --> MyGCHR : RPA
MyHRRP --> MyGCHR : manual entry
MyGCHR --> MyGCHR_to_MyGCPay : HR-specific info
MyGCHR_to_MyGCPay --> MyGCPay : HR-specific info
Phoenix_to_MyGCPay --> MyGCPay : financial and case status data
Phoenix --> Phoenix_to_MyGCPay
Phoenix --> Third_party
HRSD --> MyGCHR : manual entry
