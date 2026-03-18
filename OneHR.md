```mermaid
classDiagram
namespace Core_task {
    class task {
        +✅Name: Task
        +Usage: Base ServiceNow task table
        +number: string
        +short_description: string
        +state: integer
        +priority: integer
        +opened_at: datetime
        +assigned_to: reference
        +assignment_group: reference
        +lifecycle(action)
        +assignment(action, target)
        +routing(action)
        +sla(action)
        +relation(action, record)
        +comment(action, payload)
        +notify(channel)
        +attachment(action, fileRef)
    }
}
namespace HRSD {
    class sn_hr_core_case {
        +✅Name: HR Case
        +Usage: Main HR Table
        +number: string
        +short_description: string
        +state: integer
        +priority: integer
        +hr_service: reference
        +subject_person: reference
        +opened_for: reference
        +assignment_group: reference
        +assigned_to: reference
        +lifecycle(action)
        +routing(action)
        +template(action, templateId)
        +tasking(action, taskModel)
        +sla(action)
        +communication(action, channel)
        +security(action, scope)
    }
class conflict_of_interest_v1_rp {
        +✅Record Producer: Conflict of Interest Declaration V1
        +Category: Code of conduct and declaration of conflict of interest
        +Parent Category: Inclusivity, safety and mental health
        +Catalog: Human Resources Catalog
    +outside_activity_flag: choice
    +political_activity_flag: choice
    +assets_flag: choice
    +gifts_flag: choice
    +post_employment_flag: choice
    +relationships_flag: choice
    +summary_outside_activity: text
    +summary_political_activity: text
    +summary_assets: text
    +summary_gifts: text
    +summary_post_employment: text
    +summary_relationships: text
      +lifecycle(action)
    +routing(action)
    +tasking(action, taskModel)
 }
class conflict_of_interest_v2_rp {
 }
class sn_hr_core_case_conflict_of_interest {
 }
class  sn_hr_core_declaration {
 }
 class  sn_hr_core_coi_question_answers {
 }
    class sn_hr_core_service {
        +📋 HR Service
        +🎯 Service catalogue taxonomy
        +string name
        +string description
        +reference hr_service_type
    }
    class sn_hr_core_position {
}
class sn_hr_core_case_talent_management {
}
}

%% ══════════════════════════════
%% APPLICATION FILE
%% ══════════════════════════════
namespace app_file {
class sys_metadata {
}
}
%% ══════════════════════════════
%% CORE SERVICE CATALOG
%% ══════════════════════════════
namespace Service_Catalog {
    class sc_catalog {
        +✅name: Service Catalog
        +usage: Lists catalog definition (HR, RP, IT, etc.)
        +Title: string
        +Active: boolean
        +CatalogHomePage: string
        +sys_id: string
        +Catalog(sys_id)
        +canView(mobile, userId?)
        +getAvailableCatalog()
 }
    class sc_category {
        +✅name: Catalog Category
        +usage: List catalog categories (Hire a person, Inclusivity, etc.)
        +Title: string
        +Active: boolean
        +Parent: reference(sc_category)
        +sys_id: string
}
    class sc_cat_item_producer {
        +✅name: Record Producer
        +Usage: HR request form definition
        +name: string
        +table_name: string
        +sc_catalogs: reference
        +active: boolean
        +sys_id: string
        ---
        +producer(action)
        +variables(action, setOrVar)
        +submit(payload)
        +routing(action)
        +notify(channel)
    }
    class sc_cat_item {
    } 

%% VALIDATION NEEDED BELOW %%

    class sc_req_item {
        +✅Name: Request Item
        +Usage: One record per submitted request
        +number: string
        +cat_item: reference
        +request: reference
        +opened_for: reference
        +state: integer
        +stage: string
        +assignment_group: reference
        +assigned_to: reference
        ---
        +lifecycle(action)
        +fulfillment(action)
        +assignment(action, target)
        +routing(action)
        +approvals(action, target)
        +sla(action)
        +communication(action, channel)
        +attachment(action, fileRef)
    }

    class item_option_new {
        +📋 Variable
        +🎯 Individual field on a form
        +string name
        +string question_text
        +string type
        +boolean mandatory
        +integer order
        +reference cat_item
        +reference variable_set
    }
    class item_option_new_set {
        +📋 Variable Set
        +🎯 Reusable group of fields
        +string name
        +string sys_id
    }
    class io_set_item {
        +📋 Variable Set Link
        +🎯 Links variable sets to producers
        +reference sc_cat_item
        +reference variable_set
    }
}
%% ══════════════════════════════
%% CORE USER AND IDENTITY
%% ══════════════════════════════
namespace User_and_Identity {
    class sys_user {
        +✅Name: User Profile
        +Usage: One record per ServiceNow user
        +Source: Source: PSPC Directory via AD
        +user_name: string
        +first_name: string
        +last_name: string
        +email: string
        +phone: string
        +preferred_language: string
        +department: reference
        +company: reference
        +active: boolean
        +account(action)
        +access(action, roleOrGroup)
        +profile(action)
        +link(action, externalId)
        +notify(channel)
    }
    class sn_hr_core_profile {
        +✅Name: HR Profile
        +Usage: Employment data linked to user
        +Source: MyGCHR Job Data
        +hr_profile_number: string
        +employee_number: string
        +user: reference
        +department: reference
        +company: reference
        +status: string
        +secure_info: boolean
        +profile(action)
        +privacy(action)
        +link(action, externalId)
        +access(action, permission)
        +case(action, service)
    }
}
namespace PSPC_Org {
    class PSPC_Directory {
        +📋 PSPC Directory
        +🎯 Employee-maintained profile data
        +🔗 Syncs from Active Directory
    }
    class Active_Directory {
        +distinguishedName: string
        +objectGUID: string
        +sAMAccountName: string
        +userPrincipalName: string
        +enabled: boolean
        +account(action)
        +membership(action, groupDN)
        +placement(targetOU)
        +sync(target)
    }
}
namespace MyGCHR {
    class MyGCHR_Location {
        +📋 Location Data
        +🎯 Work location reference data
        +🔗 External system - GC
    }
    class MyGCHR_Job_Data {
        +📋 Job Data - Active
        +🎯 Active employee job records
        +🔗 External system - GC
    }
    class MyGCHR_Job_Data_Terminated {
        +📋 Job Data - Terminated
        +🎯 Terminated employee records
        +🔗 External system - GC
    }
    class MyGCHR_Position {
        +📋 Position Data
        +🎯 Position definitions
        +🔗 External system - GC
    }
}
namespace Open_Dataset {
    class Concordance_data {
        +📋 Concordance Data
        +🎯 GC-wide org concordance
        +🔗 Source: TBS Open Data
    }
    class Organization_information {
        +📋 Organization Information
        +🎯 GC-wide org reference data
        +🔗 Source: TBS Open Data
    }
}
%% ══════════════════════════════
%% ORGANIZATIONAL
%% ══════════════════════════════
namespace Core_Organizational {
    class customer_account {
        +✅Name: Customer Account
        +Usage: List of identifiers required for authentication, customer classification, and integrations - GC OrgID, Account Type, FAA Schedule, RG Codes
        +name: string
        +onboarding(registrationOp)
        +relationship(hierarchyOp)        
}
    class cmn_department {
        +✅Name: Department
        +Usage: List of all sectors L2, directorates L3 and childs of PSPC
        +Source: TBD
        +name: string
        +id: string
        +description: string
        +company: reference(core_company)
        +sys_id: string
        +hierarchy(structureOp)
        +governance(roleOp)
        +finance(mappingOp)
        +directory(queryOp)
    }
    class core_company {
        +✅Name: Company
        +Usage: List of all GoC departments and agencies
        +string name
        +parent: reference
        +identity(roleOp)
        +relationship(hierarchyOp)
    }
    class business_unit {
    +✅Name: Business Unit
    +Usage: List of all branches L1 and regions of PSPC
    +name: string
    +company: reference
    +parent: reference
    +hierarchy(structureOp)
}
    class core_company {
}
    class customer_account {
}
}
%% ══════════════════════════════
%% FINANCIAL
%% ══════════════════════════════
namespace Core_Organizational {
    class cmn_cost_center {
}
}
%% ══════════════════════════════
%% SURVEY ECOSYSTEM
%% ══════════════════════════════
namespace Core_Surveys {
    class asmt_assessment_instance {
        +✅Name: Survey Instance
        +Usage: One record per survey sent to a user
        +string number
        +reference metric_type
        +reference user
        +string state
        +datetime due_date
        +datetime expiration_date
        +integer percent_answered
        +string channel
        +string related_id_1
        +assessmentLifecycle(state)
        +notification(channelType)
        +progressTracking(metric)
        +expirationCheck(timeRule)
    }
    class asmt_assessment_instance_question {
        +✅Name: Survey Response
        +Usage: Raw answer per question per instance
        +reference instance
        +reference metric
        +string value
        +string string_value
        +string category
        +boolean is_hidden
        +responseHandling(responseAction)
        +visibilityControl(visibilityRule)
    }
    class asmt_metric_result {
        +✅Name: Survey Result
        +Usage: Calculated score - primary analytics table
        +reference instance
        +reference metric
        +decimal actual_value
        +decimal normalized_value
        +decimal scaled_value
        +decimal nps_value
        +string string_value
        +boolean passed
        +reference user
        +metricCalculation(metricOp)
    }
    class asmt_condition {
        +✅Name: Survey Trigger
        +Usage: Controls when surveys fire
        +boolean active
        +reference assessment
        +string table
        +string condition
        +boolean trigger_random
        +integer percent_random
        +triggerEvaluation(triggerOp)
    }
}
%% ══════════════════════════════
%% RELATIONSHIPS
%% ══════════════════════════════
    %% ── Inheritance ──
    task <|-- sn_hr_core_case : extends
    task <|-- sc_req_item : extends
    sc_cat_item <|-- sc_cat_item_producer: extends
    core_company <|-- customer_account: extends
    sys_metadata <|-- sc_catalog: extends
    sys_metadata <|-- sc_category: extends

    %% ── HR Case ──
    sn_hr_core_case --> sn_hr_core_service : hr_service
    sn_hr_core_case --> sn_hr_core_case_talent_management : hr_service
sn_hr_core_case --> conflict_of_interest_v1_rp : hr_service
sn_hr_core_case --> conflict_of_interest_v2_rp: hr_service
conflict_of_interest_v2_rp --> sn_hr_core_case_conflict_of_interest
sn_hr_core_case_conflict_of_interest --> sn_hr_core_declaration
sn_hr_core_declaration --> sn_hr_core_coi_question_answers
    sn_hr_core_case --> sys_user : opened_by / opened_for
    sn_hr_core_case --> sn_hr_core_profile : subject_person

    %% ── Catalog ──
    sc_catalog --> sc_category: catalog
    sc_cat_item_producer --> item_option_new : direct variables
    sc_cat_item_producer --> io_set_item : variable sets
    io_set_item --> item_option_new_set : variable_set
    item_option_new --> item_option_new_set : variable_set

    %% ── User & Identity ──
    sn_hr_core_profile --> sys_user : user
    sys_user --> cmn_department : department
    sys_user --> core_company : company
    sn_hr_core_profile --> cmn_department : department
    cmn_department --> core_company : company
    customer_account --> core_company : parent

    %% ── User & Identity ──
    cmn_department --> business_unit: business unit
    
    %% ── MyGCHR feeds ──
    MyGCHR_Job_Data --> sn_hr_core_profile : job data
    MyGCHR_Job_Data_Terminated --> sn_hr_core_profile : terminated job data
    MyGCHR_Location --> cmn_department : location data
    MyGCHR_Position --> sn_hr_core_profile : position data

    %% ── PSPC Directory feeds ──
    Active_Directory --> PSPC_Directory : syncs to
    PSPC_Directory --> sys_user : provisions

    %% ── Survey ──
    asmt_condition --> asmt_assessment_instance : triggers
    asmt_assessment_instance --> sys_user : user
    asmt_assessment_instance --> asmt_assessment_instance_question : instance
    asmt_assessment_instance --> asmt_metric_result : instance
    
