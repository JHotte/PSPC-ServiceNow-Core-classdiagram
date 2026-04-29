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
class task_SLA {
Name: task_SLA
}
class SLA_Definition {
Name: contract_SLA
}
namespace Core {
class Task {
Name: Task
}
class HR_Core_Case {
Name: sn_hr_core_case
}
}
namespace COI_1.3 {
class HR_Workforce_Administration_Case {
Name: sn_hr_core_case_workforce_admin
}
}
Sys_Audit -- Task
Sys_Audit -- HR_Core_Case
Task -- HR_Core_Case
Metric_instance -- Metric_definition: definition
HR_Core_Case -- HR_Workforce_Administration_Case
Metric_instance -- HR_Workforce_Administration_Case
task_SLA -- Task
task_SLA -- SLA_Definition: definition
