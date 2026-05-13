```mermaid
classDiagram
class sys_user {
label:user
}
class core_company {
label:Company
}
class cmn_building {
label:Building
}
class cmn_cost_center {
label:Cost Center
}
class cmn_building {
label:cmn_cost_center
}
class cmn_department {
label:Department
}
class sys_user_group {
label:Group
}
class sn_hr_integrations_source {
label:HR Integrations Source
}
class sn_hr_core_profile {
label:HR Profile
}
class ldap_server_config {
label:LDAP Server
}
class cmn_location {
label:Location
}
class sys_perspective {
label:Menu List
}
class cmn_schedule {
label:Schedule
}
class time_sheet_policy {
label:Time Sheet Policy
}
%% ----------
Linkages
%% ----------
sys_user -- cmn_building: unsued for users
sys_user -- core_company: 
sys_user -- cmn_cost_center
sys_user -- cmn_department
sys_user -- sys_user_group
sys_user -- sn_hr_integrations_source
sys_user -- sn_hr_core_profile
sys_user -- ldap_server_config
sys_user -- cmn_location
sys_user -- sys_perspective
sys_user -- cmn_schedule
sys_user -- time_sheet_policy
