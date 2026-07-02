```mermaid
classDiagram
class sys_user {
}
class sn_hr_core_profile {
}
class sn_hr_core_service {
1st level organization_HR Cases types
+L3
Direct Deposit(Record Producer)
}
class sn_hr_core_topic_detail {
Pay (L2)
}
class sn_hr_core_topic_category {
Pay (L1)
}
class task {
+Assignment group/Assigned to
+Status
}
class sn_hr_core_case {
}
class sn_hr_core_case_payroll {
}
class question_answers {
+Variable Sets answers
+Direct Variables answers
}
class task_SLA {
+SLA Measurement
}
class contract_SLA {
+SLA Definition
}
class metric_instance {
+Metric Measurement
}
class metric_definition {
+Metric Definition
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
sn_hr_core_case --> sn_hr_core_service: reference
sn_hr_core_service --> sn_hr_core_topic_detail : references
sn_hr_core_topic_detail --> sn_hr_core_topic_category : references
