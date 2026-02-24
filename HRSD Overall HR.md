```mermaid
classDiagram
namespace HRSD {
class sn_hr_core_case
class sn_hr_core_profile {
HR Profiles
}
%% category %%
class sn_hr_core_case_workforce_admin {
Conflict of Interest Declaration (HRSD catalog)
}
%% category %%
class sn_hr_core_case_talent_management {
Departure and Early end of Employment (HRSD catalog)
Pay, benefits and pension plan
}
class sn_hr_core_job {
Job
}
class sn_hr_core_position {
Positions
}
class sn_hr_core_position_attribute {
Position Attributes
}
class sn_hr_integr_fw_source {
Integration Source
}
}
%% Core
namespace Core {
class sm_order {
Requester / Assigned workgroup / Priority / Status()
}
class wm_order {
Priority / Description / Assignment group()
}
class cmn_location
class core_country {
Country
class cmn_department
}
}

%% Core_identity group
namespace Core_identity {
class sys_user {
Stores user profiles
}
class sys_user_group {
Stores groups
}
class sys_user_role {
Stores roles
}
}
%% Core Task & Work Management Core Tables
namespace Core_task_and_Work_Management {
class task {
All task‑based records
}
class incident {
Incident records
}
class problem {
Problem records
}
class change_request {
Change Requests
}
}

%% Relationships - Core_identity
sys_user -- sys_user_group : reference

%% Relationships - Core_task_and_Work_Management
task -- incident : extend
task -- problem : extend
task -- change_request : extend


%% Other
sn_hr_core_case_workforce_admin -- sn_hr_core_case: extend
sn_hr_core_profile -- sys_user: reference
sn_hr_core_profile -- cmn_location: reference
sn_hr_core_profile -- sn_hr_core_position: reference
sn_hr_core_profile -- core_country: reference
sn_hr_core_profile -- sn_hr_core_position_attribute: reference
sn_hr_core_profile -- sn_hr_integr_fw_source: reference
sn_hr_core_profile -- sn_hr_core_job: reference
sn_hr_core_case_talent_management -- sn_hr_core_case: extend
sn_hr_core_case_talent_management -- cmn_department: reference
sn_hr_core_case_talent_management -- cmn_location: reference
sn_hr_core_case_workforce_admin -- task : reference
sn_hr_core_case_workforce_admin -- sn_hr_core_case : reference
sm_order -- wm_order : extend
sm_order -- task : extend
hr_case -- sm_order : extend
