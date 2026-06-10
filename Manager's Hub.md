```mermaid
classDiagram
%% Manager's Hub %%
namespace Manager_Hub {
class sn_mh_team_data_config {
Label: Team Data Configuration
Purpose: Displays employee details on manager's dashboard
Role: Filters by conditions & users fields
}
class sn_mh_team_column_config {
Label: Teams Column Configuration
Purpose: Displays variables that shows on 'Your Team'
Role: Includes custom scripts (i.e. COI Status)
}
class sn_mh_important_dates_config {
Label: Important dates configuration
Date-based widgets
Employment Start Date (script)
}
class sn_mh_team_daily_stat {
Label: Team Daily Stats
Status: TBD
}
class sn_mh_team_requests_config {
Status: TBD 
}
class sn_mh_team_filter_config { 
}
}
%% Core ServiceNow %%
namespace Core {
class sys_user {
Label: User
Source: EntraID/PSPC Directory
Active and not contractors/consultants only (script)
}
}
%% HRSD %%
namespace HRSD {
class sn_hr_core_case_workforce_admin {
}
class sn_employee_profile {
Label: Employee profile
}
class sn_hr_core_profile {
Label: HR Pofile
Source: MyGCHR
Status: Active
}
class sn_hr_core_emp_time_off {
Status: Inactive
}
class sn_hr_core_leave_of_absence {
Status: Inactive
}
class sn_hr_core_position {
}
class sn_hr_core_conflict_of_interest {
Label: Conflict of interest
}
}
%% Links %%
sn_mh_team_data_config -- sn_employee_profile: "New hire / Employee profile / Leaving soon"
sn_mh_team_data_config -- sn_hr_core_case_workforce_admin : "Coi done"
sn_mh_team_data_config -- sn_hr_core_emp_time_off : "PTO"
sn_mh_team_data_config -- sn_hr_core_leave_of_absence : Upcoming and actual leave
sn_mh_team_data_config -- sn_hr_core_profile: HR Profile
sn_mh_team_data_config -- sys_user: "User records"
sn_mh_team_data_config -- sn_hr_core_conflict_of_interest: "COI Status Script"
sn_mh_team_data_config -- sn_mh_team_data_config: "Filter configs"
sn_employee_profile -- sn_hr_core_profile: HR Profile
sn_mh_important_dates_config -- sn_hr_core_emp_time_off
sn_mh_important_dates_config -- sn_hr_core_profile
