```mermaid
classDiagram
namespace Core {
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
        ---
        +lifecycle(action)            %% create | update | close | cancel | reopen
        +assignment(action, target)   %% assign(user) | assign(group) | unassign
        +routing(action)              %% evaluateRules | route | reassign
        +sla(action)                  %% start | pause | stop | recalc
        +relation(action, record)     %% linkParent | linkChild | unlink
        +comment(action, payload)     %% addWorkNote | addCustomerNote
        +notify(channel)              %% email | chat | mobilePush | teams
        +attachment(action, fileRef)  %% add | remove
    }
}
namespace HRSD_Core {
    class sn_hr_core_case {
        +✅Name: HR Case
        +Goal: Every HR request creates one record here
        +number: string
        +short_description: string
        +state: integer
        +priority: integer
        +hr_service: reference
        +subject_person: reference
        +opened_for: reference
        +assignment_group: reference
        +assigned_to: reference
        ---
        +lifecycle(action)               %% open | update | resolve | close | reopen | cancel
        +routing(action)                 %% evaluate | autoAssign | reassign | escalate
        +template(action, templateId)    %% apply | remove
        +tasking(action, taskModel)      %% generate | sync | closeChildren
        +sla(action)                     %% start | pause | stop | recalc
        +communication(action, channel)  %% notify | requestInfo | acknowledge
        +security(action, scope)         %% restrict | relax (COE/ACL/visibility)

    }
    class sn_hr_core_service {
        +📋 HR Service
        +🎯 Service catalogue taxonomy
        +string name
        +string description
        +reference hr_service_type
    }
}
namespace HRSD_Specific {
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
namespace Service_Catalog {
    class sc_cat_item_producer {
        +📋 Record Producer
        +🎯 HR request form definition
        +string name
        +string table_name
        +reference sc_catalogs
        +boolean active
    }
    class sc_req_item {
        +📋 Request Item
        +🎯 One record per submitted request
        +string number
        +reference cat_item
        +reference request
        +reference opened_for
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
        +Name: Department
        +Usage: Organizational unit reference
        +Source: TBD
        +string name
        +string id
        +reference parent
        +reference company
    }
    class core_company {
        +Name: Company
        +Usage: Legal entity reference
        +string name
        +string stock_symbol
    }
}
%% ══════════════════════════════
%% SURVEY ECOSYSTEM
%% ══════════════════════════════
namespace Core_Surveys {
    class asmt_assessment_instance {
        +Name: Survey Instance
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
        +launchAssessment()
        +sendNotification()
        +trackProgress()
        +closeAssessment()
        +calculateCompletionPercent()
        +expireIfOverdue()
    }
    class asmt_assessment_instance_question {
        +Name: Survey Response
        +Usage: Raw answer per question per instance
        +reference instance
        +reference metric
        +string value
        +string string_value
        +string category
        +boolean is_hidden
        +captureResponse()
        +validateAnswer()
        +hideOrShowBasedOnLogic()
        +storeStringValue()
    }
    class asmt_metric_result {
        +Name: Survey Result
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
        +calculateMetricValue()
        +normalizeScore()
        +applyScalingRules()
        +computeNPS()
        +recordPassFail()
    }
    class asmt_condition {
        +Name: Survey Trigger
        +Usage: Controls when surveys fire
        +boolean active
        +reference assessment
        +string table
        +string condition
        +boolean trigger_random
        +integer percent_random
        +evaluateTrigger()
        +matchRecordConditions()
        +startAssessmentInstance()
        +selectRandomSample()
    }
}
%% ══════════════════════════════
%% RELATIONSHIPS
%% ══════════════════════════════
    %% ── Inheritance ──
    task <|-- sn_hr_core_case : extends
    task <|-- sc_req_item : extends

    %% ── HR Case ──
    sn_hr_core_case --> sn_hr_core_service : hr_service
    sn_hr_core_case --> sys_user : opened_by / opened_for
    sn_hr_core_case --> sn_hr_core_profile : subject_person

    %% ── Catalog ──
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
    
