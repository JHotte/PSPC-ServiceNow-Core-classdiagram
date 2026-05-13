```mermaid
classDiagram
namespace Global_Catalog {
class sc_catalog {
Name: Catalog
}
class sc_category {
Name: Category
}
class sc_cat_item_producer {
Name: Record Producer
}
}
namespace Global {
class task {
Name: task
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
class contract_SLA {
Name: SLA Definition
}
class sys_metadata {
Name: Application File
}
}
namespace HR_Core_Transactional {
class sn_hr_core_case_payroll {
Name: HR Payroll Case
T4, Relevé 1 and Relevé 2(RP)
Pay increment adjustment(RP)
Overtime(RP)
Voluntary cash out(RP)
Copy of pay file(RP)
Deductions(RP)
Overpayment(RP)
Lost or stolen paycheque(RP)
Severance Pay(RP)
}
class sn_hr_core_case_benefits {
Name: HR Benefits Case
Public Service Health Care Plan PSHCP(RP)
Public Service Dental Care Plan PSDCP(RP)
Disability insurance and long-term disability(RP)
Public Service Management Insurance Plan PSMIP(RP)
Pension Plan(RP)

}
class sn_hr_core_case {
Name: HR Case
}

}
namespace HR_Core_UX {
class sn_hr_core_service {
Name: HR Service
}
class sn_hr_core_template {
Name: HR Template
}
class sn_hr_core_criteria {
Name: HR Criteria
}
}
Metric_instance -- Metric_definition: defnitions and configurations
Metric_instance -- task: metric capture
task_SLA -- contract_SLA: defnitions and configurations
task_SLA -- task: SLA capture
sn_hr_core_service -- sys_metadata: extends
sn_hr_core_service -- sn_hr_core_case: defines case type and behaviour
task -- sn_hr_core_case
sn_hr_core_case -- sn_hr_core_case_payroll
sn_hr_core_case -- sn_hr_core_case_benefits
sc_cat_item_producer --> "1..*" sn_hr_core_service
sc_cat_item_producer -- sn_hr_core_case
sn_hr_core_criteria -- sys_metadata: extends
sn_hr_core_service  -- sn_hr_core_template: HR Service to HR Template
sc_catalog -- sc_category
sc_category -- sc_cat_item_producer
