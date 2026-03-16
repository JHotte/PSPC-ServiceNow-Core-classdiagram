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
namespace HRSD_Core {
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
    class sn_hr_core_service {
        +📋 HR Service
        +🎯 Service catalogue taxonomy
        +string name
        +string description
        +reference hr_service_type
    }
}
%% ══════════════════════════════
%% COI
%% ══════════════════════════════
namespace COI_Specific {
    class sn_hr_core_conflict_of_interest {
        +📋 Conflict of Interest
    }
    class sn_hr_core_declaration {
        +📋 COI Declaration
    }
    class sn_hr_core_coi_question_answers {
        +📋 COI Question Answers
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
        +Title: string                      %% descriptive catalog name
        +Active: boolean                    %% visible to end users when true
        +CatalogHomePage: string            %% content page URL for “Catalog Home” navigation 
        +sys_id: string                     %% unique identifier (standard on all SN tables)
         ---
        +Catalog(sys_id)                    %% instantiate Catalog object using sys_id
        +canView(mobile, userId?)           %% evaluate if user can view catalog (mobile/desktop) 
        +getAvailableCatalog()              %% fetch earliest available active catalog for user
 }
    class sc_category {
        +✅name: Catalog Category
        +usage: List catalog categories (Hire a person, Inclusivity, etc.)
        +Title: string                       %% category name displayed to users
        +Active: boolean                     %% inactive categories hide entire subtrees from end users
        +Parent: reference(sc_category)      %% enables category hierarchy (nested categories)
        +sys_id: string                      %% unique identifier (standard on all SN tables)
        ---
}
    class sc_cat_item_producer {
        +✅name: Record Producer
        +Usage: HR request form definition
        +name: string
        +table_name: string            %% target table (e.g., sn_hr_core_case)
        +sc_catalogs: reference
        +active: boolean
        +sys_id: string
        ---
        +producer(action)                 %% enable | disable | retire | publish
        +variables(action, setOrVar)      %% add | remove | attachSet | detachSet
        +submit(payload)                  %% create target record from variables
        +routing(action)                  %% evaluateRules | route | setAssignment
        +notify(channel)                  %% email | chat | mobile
    }
    class sc_cat_item {
    } 

%% VALIDATION NEEDED BELOW %%

    class sc_req_item {
        +✅Name: Request Item
        +Usage: One record per submitted request
        +number: string
        +cat_item: reference        %% originating catalog item
        +request: reference         %% parent REQ (sc_request)
        +opened_for: reference
        +state: integer
        +stage: string
        +assignment_group: reference
        +assigned_to: reference
        ---
        +lifecycle(action)               %% submit | update | complete | close | cancel | reopen
        +fulfillment(action)             %% generateTasks | sync | closeChildren
        +assignment(action, target)      %% assign(user|group) | unassign
        +routing(action)                 %% evaluateRules | route | escalate
        +approvals(action, target)       %% request | approve | reject | reassign
        +sla(action)                     %% start | pause | stop | recalc
        +communication(action, channel)  %% notify | requestInfo | acknowledge
        +attachment(action, fileRef)     %% add | remove
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
        ---
        +account(action)              %% create | activate | deactivate | lock | unlock | resetPassword
        +access(action, roleOrGroup)  %% grant | revoke (roles / groups)
        +profile(action)              %% update | setPreference | setLocale
        +link(action, externalId)     %% link | unlink (e.g., HR Profile / AD / IAM)
        +notify(channel)              %% email | sms | teams | mobilePush
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
        +status: string           %% e.g., active | inactive
        +secure_info: boolean     %% conceptual flag for sensitive data
        ---
        +profile(action)                 %% create | update | deactivate | merge
        +privacy(action)                 %% setConsent | revokeConsent | mask | unmask
        +link(action, externalId)        %% link | unlink (User/AD/IAM)
        +access(action, permission)      %% grant | revoke (secure info scopes)
        +case(action, service)           %% create | view | correlate (launch HR case)

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
        +account(action)              %% create | disable | enable | unlock | resetPassword
        +membership(action, groupDN)  %% add | remove
        +placement(targetOU)          %% move object to OU
        +sync(target)                 %% ServiceNow | HRSD | IAM
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
    class cmn_department {
        +✅Name: Department
        +Usage: List of all sectors (level 2), directorates (level 3) and subsequent 
        +Source: TBD
        +name: string                         %% department name (name_value)
        +id: string                           %% department ID/code (id_value / code)
        +description: string                  %% long description (description_value)
        +company: reference(core_company)     %% associated company (company_value)
        +sys_id: string                       %% unique identifier (sys_id_value)
        ---
        +hierarchy(structureOp)               %% assignParent | getAncestors | getDescendants
        +governance(roleOp)                   %% setDeptHead | setPrimaryContact | assignCompany
        +finance(mappingOp)                   %% linkCostCenter | updateCostCenter
        +directory(queryOp)                   %% lookupByCode | lookupByName | listSubdepartments
    }
    class core_company {
        +✅Name: Company
        +Usage: Legal entity reference
        +string name
        +string stock_symbol
    }
    class business_unit {
}
    class position {
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
        ---
        +assessmentLifecycle(state)          %% launch | close | expire
        +notification(channelType)           %% email | sms | push
        +progressTracking(metric)            %% computeCompletion | updateProgress
        +expirationCheck(timeRule)           %% expireIfOverdue
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
        ---
        +responseHandling(responseAction)     %% capture | validate | store
        +visibilityControl(visibilityRule)    %% hide | show | evaluateLogic
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
        ---
        +metricCalculation(metricOp)          %% calculate | normalize | scale | computeNPS | passFail
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
        ---
        +triggerEvaluation(triggerOp)         %% evaluate | matchConditions | createInstance | selectRandomSample
    }
}
%% ══════════════════════════════
%% RELATIONSHIPS
%% ══════════════════════════════
    %% ── Inheritance ──
    task <|-- sn_hr_core_case : extends
    task <|-- sc_req_item : extends
    sc_cat_item <|-- sc_cat_item_producer: extends
    sys_metadata <|-- sc_catalog: extends
    sys_metadata <|-- sc_category: extends

    %% ── HR Case ──
    sn_hr_core_case --> sn_hr_core_service : hr_service
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
    
