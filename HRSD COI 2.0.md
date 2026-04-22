```mermaid
classDiagram
class Sys Audit {
Name: sys_audit
Timestamps(attributes)
}
namespace Core {
class Task {
Name: Task
}
class HR Core Case {
Name: sn_hr_core_case
}
}
namespace COI 2.0 {
class Conflict of interest {
COI case header
Name: sn_hr_core_conflict_of_interest
Number(COIXXXX)
File_Status()
}
class COI Declaration {
Situation screening - what applies?
Name: sn_hr_core_declaration
One declaration generated per type of declartaion
Number(DECXXXX)
File_Status()
}
class COI Situation {
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
class COI 2.0 DB View {
Name: sn_hr_core_coi2_db_view
}
Sys Audit -- Task
Sys Audit -- HR Core Case
Sys Audit -- Conflict of interest
Sys Audit -- COI Declaration
Sys Audit -- COI Situation
Task -- HR Core Case
HR Core Case -- Conflict of interest
Conflict of interest -- COI Declaration: COI declaration
Conflict of interest -- COI Situation
COI Declaration -- COI Situation : situation details
COI 2.0 DB View -- Conflict of interest: reporting view
COI 2.0 DB View -- COI Declaration: reporting view
COI 2.0 DB View -- COI Situation: reporting view
