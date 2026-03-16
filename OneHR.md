```mermaid
classDiagram
namespace Core {
    %% ══════════════════════════════
    %% CORE SERVICENOW BASE
    %% ══════════════════════════════
    class task {
        +string number
        +string short_description
        +string description
        +integer state
        +integer priority
        +datetime opened_at
        +datetime closed_at
        +string contact_type
        +reference opened_by
        +reference assigned_to
        +reference assignment_group
        +list watch_list
        +string sys_class_name
    }
    }

    %% ══════════════════════════════
    %% HRSD CORE
    %% ══════════════════════════════
    class sn_hr_core_case {
        +reference hr_service
        +reference subject_person
        +reference opened_for
        +string u_subject_person
    }

    class sn_hr_core_service {
        +string name
        +string description
        +reference hr_service_type
    }

    %% ══════════════════════════════
    %% SERVICE CATALOG
    %% ══════════════════════════════
    class sc_cat_item_producer {
        +string name
        +string table_name
        +reference sc_catalogs
        +boolean active
    }

    class sc_req_item {
        +string number
        +reference cat_item
        +reference request
        +reference opened_for
    }

    class item_option_new {
        +string name
        +string question_text
        +string type
        +boolean mandatory
        +integer order
        +reference cat_item
        +reference variable_set
    }

    class item_option_new_set {
        +string name
        +string sys_id
    }

    class io_set_item {
        +reference sc_cat_item
        +reference variable_set
    }
namespace User_and_identity {
    %% ══════════════════════════════
    %% USER & IDENTITY
    %% ══════════════════════════════
    class sys_user {
        +string user_name
        +string first_name
+string last_name
        +string email
        +string phone
        +string preferred_language
        +reference department
        +reference company
    }

    class sn_hr_core_profile {
        +reference user
        +string hr_profile_number
        +string employee_number
        +reference department
        +reference company
    }
}
namespace Organizational {
    %% ══════════════════════════════
    %% ORGANIZATIONAL
    %% ══════════════════════════════
    class cmn_department {
        +string name
        +string id
        +reference parent
        +reference company
    }

    class core_company {
        +string name
        +string stock_symbol
    }
}
namespace Surveys {
    %% ══════════════════════════════
    %% SURVEY ECOSYSTEM
    %% ══════════════════════════════
    class asmt_assessment_instance {
        +string number
        +reference metric_type
        +reference user
        +string state
        +datetime due_date
        +datetime expiration_date
        +integer percent_answered
        +string channel
        +string related_id_1
    }

    class asmt_assessment_instance_question {
        +reference instance
        +reference metric
        +string value
        +string string_value
        +string category
        +boolean is_hidden
    }

    class asmt_metric_result {
        +reference instance
        +reference metric
        +decimal actual_value
        +decimal normalized_value
        +decimal scaled_value
        +decimal nps_value
        +string string_value
        +boolean passed
        +reference user
    }

    class asmt_condition {
        +boolean active
        +reference assessment
        +string table
        +string condition
        +boolean trigger_random
        +integer percent_random
    }
}
    %% ══════════════════════════════
    %% RELATIONSHIPS
    %% ══════════════════════════════

    %% Inheritance
    task <|-- sn_hr_core_case : extends
    task <|-- sc_req_item : extends

    %% HR Case relationships
    sn_hr_core_case --> sn_hr_core_service : hr_service
    sn_hr_core_case --> sys_user : opened_by / opened_for
    sn_hr_core_case --> sn_hr_core_profile : subject_person

    %% Catalog structure
    sc_cat_item_producer --> item_option_new : direct variables
    sc_cat_item_producer --> io_set_item : variable sets
    io_set_item --> item_option_new_set : variable_set
    item_option_new --> item_option_new_set : variable_set

    %% User & identity
    sn_hr_core_profile --> sys_user : user
    sys_user --> cmn_department : department
    sys_user --> core_company : company
    sn_hr_core_profile --> cmn_department : department
    cmn_department --> core_company : company

    %% Survey
    asmt_condition --> asmt_assessment_instance : triggers
    asmt_assessment_instance --> sys_user : user
    asmt_assessment_instance --> asmt_assessment_instance_question : instance
    asmt_assessment_instance --> asmt_metric_result : instance
