```mermaid
classDiagram
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
class SLA {
Sets of tables
task_sla table (measurement)
contract_sla table (definition)
}
class metric {
Sets of tables 
metric_instance table (measurement)
metric_definition table (definition)
}
class catalog_client_facing {
Sets of tables
sc_catalog table (Catalog L1)
sc_category table (Category/Sub-Category L2/L3)
sc_cat_item_producer table (Record Producer L4)
}
class sys_attachment {
+Request Attachments
}
task -- sn_hr_core_case: extends
sn_hr_core_case <|-- sn_hr_core_case_payroll: extends
sn_hr_core_case_payroll -- question_answers: table sys ID
sn_hr_core_case_payroll -- sys_attachment: request attachments
task -- SLA
sn_hr_core_case -- metric
catalog_client_facing -- sn_hr_core_case 
