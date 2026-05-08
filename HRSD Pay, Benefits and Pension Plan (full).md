```mermaid
classDiagram
namespace Global {
class task {
Name: task
}
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
class contract_SLA {
Name: SLA Definition
}
}
namespace Human_Resources_Core {
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
%% -----------
%% Core -----
%% -----------
Metric_instance -- Metric_definition
Metric_instance -- Sys_Audit
task_SLA -- Sys_Audit
task_SLA -- contract_SLA
task -- sn_hr_core_case: number
sn_hr_core_case -- sn_hr_core_case_payroll: number
sn_hr_core_case -- sn_hr_core_case_benefits: number
task -- sn_hr_core_case_payroll: number
