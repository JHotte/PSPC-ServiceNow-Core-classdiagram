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
metric_definition -- metric_instance
