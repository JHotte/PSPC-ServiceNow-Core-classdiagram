```mermaid
classDiagram
namespace HR_Case {
class sn_hr_core_case {
HR Case
}}
namespace COI_form {
class sn_hr_core_conflict_of_interest{
Conflict of Interest
}
}
namespace Declaration_form {
class sn_hr_core_declaration{
COI Declaration
}
}
namespace Custom_table {
class test3
}
namespace Situation {
class sn_hr_core_coi_question_answers{
}
}
namespace ACL {
class test2{
}
}
sn_hr_core_case .. sn_hr_core_conflict_of_interest : extend
