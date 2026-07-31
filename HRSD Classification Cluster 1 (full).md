'''mermaid
classDiagram
class Metric_instance {
Name: Metric_instance
}
class task_SLA {
Name: task_SLA
}
namespace Core {
class Task {
Name: Task
}
class HR_Core_Case {
Name: sn_hr_core_case
}
}
namespace COI_1point3 {
class HR_Workforce_Administration_Case {
Name: sn_hr_core_case_workforce_admin
}
}
Task -- HR_Core_Case
HR_Core_Case -- HR_Workforce_Administration_Case
Metric_instance -- HR_Workforce_Administration_Case
Metric_instance -- HR_Core_Case
task_SLA -- Task
