```mermaid
classDiagram
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
Name: sn_hr_core_conflict_of_interest
}
class COI Declaration {
Name: sn_hr_core_declaration
}
class COI Situation {
Name: sn_hr_core_coi_question_answers
}
}
Task -- HR Core Case
HR Core Case -- Conflict of interest
Conflict of interest -- COI Declaration
COI Declaration -- COI Situation
