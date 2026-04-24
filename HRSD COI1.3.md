```mermaid
classDiagram
class Sys_Audit {
Name: sys_audit
Timestamps(attributes)
}
class Metric_instance {
Name: Metric_instance
Records of measures of determined data points
DEC-Time_to_respond_MED_HIGH(COI_File_Status_changes)
DEC-Time_to_respond_LOW(COI_FIle_Status_changes)
DEC-Time_to_respond(COI_File_Status_changes))
SIT-Time_between_each_state(COI_File_Status_changes)
SIT-Time_to_respond_LOW(COI_File_Status_changes)
SIT-Time_to_assign(assigned_to)
SIT-Time_to_respond_MED_HIGH(COI_File_Status_changes))
}
class Metric_definition {
Name: Metric_definition
Rules to measure determined data points
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
COI case header
Name: sn_hr_core_conflict_of_interest
Number(COIXXXX)
File_Status()
}
class COI_Declaration {
Situation screening - what applies?
Name: sn_hr_core_declaration
One declaration generated per type of declartaion
Number(DECXXXX)
File_Status()
}
class COI_Situation {
Situation detail - details
Name: sn_hr_core_coi_question_answers
One situation generated per type of situation - only problematic declarations have situations generated
Number(SITXXXX)
Declaration_type()
File_Status()
Description()
Benchmark()
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
