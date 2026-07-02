```mermaid
classDiagram
class task {
High-level and general informations
+Assignment group/Assigned to
+Status
}
class sn_hr_core_case {
HR-Specific level informations
}
class hr_specific_tables {
Specific HR-related tables specific to transactions
Conflict of interest V1.3(sn_hr_core_case_workforce_admin)
Conflict of interest V2(sn_hr_core_case_conflict_of_interest)
Pay(sn_hr_core_case_payroll)
Benefits & Pension Plan(sn_hr_core_case_benefits)
Departure(sn_hr_core_case_talent_management)
Classification and organizational structure(sn_hr_core_case_workforce_admin)
}
class question_answers {
+Variable Sets answers
+Direct Variables answers
}
class SLA {
Sets of tables to manage SLA measurement
task_sla table (measurement)
contract_sla table (definition)
}
class metric {
Sets of tables to manage metric measurement
metric_instance table (measurement)
metric_definition table (definition)
}
class catalog_client_facing {
Sets of tables to manage catalog (client facing) architecture
sc_catalog table (Catalog L1)
sc_category table (Category/Sub-Category L2/L3)
sc_cat_item_producer table (Record Producer L4)
}
class catalog_agent_facing {
Sets of tables to manage catalog (agent facing) architecture
sn_hr_core_topic_category table (Category L2)
sn_hr_core_topic_detail table (Sub-Category L3)
sn_hr_core_service table (Record Producer L4)
}
class sys_attachment {
+Request Attachments
}
task -- sn_hr_core_case: extends
sn_hr_core_case <|-- hr_specific_tables: extends
hr_specific_tables -- question_answers: table sys ID
hr_specific_tables -- sys_attachment: request attachments
task -- SLA
sn_hr_core_case -- metric
catalog_client_facing -- sn_hr_core_case
catalog_agent_facing -- sn_hr_core_case
catalog_agent_facing -- catalog_client_facing
