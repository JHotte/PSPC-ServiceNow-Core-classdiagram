```mermaid
classDiagram
namespace SN_Core {
class tbd {
}
}
namespace PSPC_Governed_Core {
class cmn_location {
}
class core_company {
}
class business_unit {
}
class cmn_cost_center {
}
class cmn_location {
}
}
namespace Platform_Core {
class sys_user {
}
class cmn_schedule {
}
class sys_user_group {
}
class sys_user_role {
}
}
namespace HRSD_Core {
class sn_hr_core_position {
}
class sn_hr_core_profile {
}
class sn_hr_core_case {
}
}
namespace HRSD_Catalogue_COI {
class sn_hr_core_conflict_of_interest {
}
class sn_hr_core_declaration {
}
class sn_hr_core_coi_question_answers {
}
class sn_hr_core_coi2_db_view {
}
}
namespace HRSD_Catalogue_Pay_Pension_Benefits {
class sn_hr_core_case_payroll {
}
class sn_hr_core_case_benefits {
}
}
%% Links %%
sys_user -- sn_hr_core_profile
%% Links COI %%
sn_hr_core_conflict_of_interest -- sn_hr_core_declaration
sn_hr_core_conflict_of_interest -- sn_hr_core_coi_question_answers
%% Links Case Catalogue
sn_hr_core_case -- sn_hr_core_case_payroll
sn_hr_core_case -- sn_hr_core_case_benefits
