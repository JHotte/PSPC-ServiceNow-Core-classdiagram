```mermaid
classDiagram
namespace hrsd {
class sn_hr_core_case {
Name: HR Core Case
}
class sn_hr_core_case_benefits {
Name: HR Benefits Case
}
class sn_hr_core_case_payroll {
Name: HR Payroll Case
}
class sn_hr_core_case_workforce_admin {
Name: HR Workforce Admin Case
}
class sn_hr_core_task {
Name: HR Tasks
}
}
class metric_definition {
Name: Metric Definition
}
class metric_instance {
Name: Metric Instance
}
namespace hrsd.COI {
class sn_hr_core_declaration {
Name: COI Declaration
}
class sn_hr_core_coi_question_answers {
Name: COI Situations
}
}
sn_hr_core_case -- metric_definition
sn_hr_core_case_benefits -- metric_definition
sn_hr_core_case_payroll -- metric_definition
sn_hr_core_case_workforce_admin -- metric_definition
sn_hr_core_task -- metric_definition
sn_hr_core_declaration -- metric_definition
sn_hr_core_coi_question_answers -- metric_definition
metric_definition -- metric_instance
