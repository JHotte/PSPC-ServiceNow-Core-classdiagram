```mermaid
classDiagram
namespace Manager_Hub {
class sn_mh_team_data_config {
Team Data Configuration
Displays employee details on manager's dashboard
}
class sn_mh_team_column_config {
Teams Column Configuration
Displays variables that shows on 'Your Team'
}
}
class sn_employee_profile {
}
class sys_user {
}
class sn_hr_core_profile {
Source: MyGCHR
}
class sn_hr_core_emp_time_off {
}
class sn_hr_core_emp_time_off {
}
class sn_hr_core_leave_of_absence {
}
class coi_completion {
}
%% Links %%
sn_mh_team_data_config -- sn_employee_profile: New hire / Employee profile / Leaving soon
sn_mh_team_data_config -- sn_hr_core_case_workforce_admin : Coi done
sn_mh_team_data_config -- sn_hr_core_emp_time_off : PTO
sn_mh_team_data_config -- sn_hr_core_leave_of_absence : Upcoming and actual leave
sn_mh_team_data_config -- sn_hr_core_profile: HR Profile
sn_mh_team_data_config -- sys_user: User
sn_mh_team_data_config -- coi_completion: Coi completion
