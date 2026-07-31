```mermaid
classDiagram
namespace hrsd {
class sn_hr_core_case {
}
class sn_hr_core_case_benefits {
}
class sn_hr_core_case_payroll {
}
class sn_hr_core_case_workforce_admin {
}
class sn_hr_core_task {
}
}
class metric_definition {
}
class metric_instance {
    +id (Sys ID of Case)
    +definition (Sys ID of Definition)
}
namespace hrsd_COI {
class sn_hr_core_declaration {
}
class sn_hr_core_coi_question_answers {
}
}

%% Corrected Relationships: Cases point to Instances, Instances point to Definitions
sn_hr_core_case --> metric_instance : tracked by
sn_hr_core_case_benefits --> metric_instance : tracked by
sn_hr_core_case_payroll --> metric_instance : tracked by
sn_hr_core_case_workforce_admin --> metric_instance : tracked by
sn_hr_core_task --> metric_instance : tracked by
sn_hr_core_declaration --> metric_instance : tracked by
sn_hr_core_coi_question_answers --> metric_instance : tracked by

metric_instance --> metric_definition : defines


