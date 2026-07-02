```mermaid
classDiagram
class sys_user {
}
class sn_hr_core_profile {
}
class task {
+Assignment group/Assigned to
+Status
}
class sn_hr_core_case {
}
class catalog
class sn_hr_core_case_payroll {
}
class question_answers {
+Variable Sets answers
+Direct Variables answers
}
class SLA {
task_sla table (measurement)
contract_sla table (definition)
}
class metric { 
metric_instance table (measurement)
metric_definition table (definition)
}
class sys_attachment {
+Request Attachments
}
task -- sn_hr_core_case: extends
sn_hr_core_case <|-- sn_hr_core_case_payroll: extends
sn_hr_core_case_payroll -- question_answers: table sys ID
sn_hr_core_case_payroll -- sys_attachment: request attachments
task_SLA -- contract_SLA
task -- task_SLA
metric_definition -- metric_instance
metric_instance -- sn_hr_core_case
