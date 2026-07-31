```mermaid
classDiagram
class metric_instance {
Name: Metric instance
}
class task_SLA {
Name: task SLA
}
namespace hrsd {
class sn_hr_core_case {
Name: HR Core Case
}
class hr location code {
Name: hr location code
}
class sn_hr_core_position {
Name: Position
Use: Identification of position of delegated manager and position no. to be modified
}
class sn_hr_core_case_workforce_admin {
Name: HR Workforce Admin Case
}
}
namespace core {
class task {
Name: Task
}
class sys_user {
Name: Sys User
Use: Identification of Requester, Delegated, etc.
}
}
task -- sn_hr_core_case
sn_hr_core_case -- sn_hr_core_case_workforce_admin
metric_instance -- sn_hr_core_case_workforce_admin
metric_instance -- sn_hr_core_case
task_SLA -- task
