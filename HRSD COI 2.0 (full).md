```mermaid
classDiagram
class Sys_Audit {
Name: sys_audit
}
class Metric_instance {
Name: Metric_instance
}
class Metric_definition {
Name: Metric_definition
}
namespace Core {
class Task {
Name: Task
}
class HR_Core_Case {
Name: sn_hr_core_case
}
}
namespace COI_2_0 {
class Conflict_of_interest {
Name: sn_hr_core_conflict_of_interest
}
class COI_Declaration {
Name: sn_hr_core_declaration
}
class COI_Situation {
Situation detail - details
Name: sn_hr_core_coi_question_answers
}
}
class COI_2_0_DB_View {
Name: sn_hr_core_coi2_db_view
}
Sys_Audit -- Task
Sys_Audit -- HR_Core_Case
Sys_Audit -- Conflict_of_interest
Sys_Audit -- COI_Declaration
Sys_Audit -- COI_Situation
Task -- HR_Core_Case
HR_Core_Case -- Conflict_of_interest
Conflict_of_interest -- COI_Declaration: COI declaration
Metric_instance -- COI_Situation: metrics
Metric_instance -- COI_Declaration: metrics
Conflict_of_interest -- COI_Situation
COI_Declaration -- COI_Situation : situation details
COI_2_0_DB_View -- Conflict_of_interest: reporting view
COI_2_0_DB_View -- COI_Declaration: reporting view
COI_2_0_DB_View -- COI_Situation: reporting view
Metric_instance -- Metric_definition: definition
