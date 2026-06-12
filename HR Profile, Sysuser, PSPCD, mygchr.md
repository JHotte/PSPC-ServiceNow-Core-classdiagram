```mermaid
classDiagram
namespace ServiceNow {
class sn_hr_core_profile {
}
class sys_user {
}
}
class PSPC_Directory {
}
class EntraID {
}
class MyGCHR {
}
PSPC_Directory --> EntraID: Direct Supervisor
EntraID --> sys_user: Direct Supervisor
MyGCHR --> sn_hr_core_profile: S34 Delegation
MyGCHR --> sn_hr_core_profile: Language
MyGCHR --> sn_hr_core_profile: Home informations (address, city, phone, email)
MyGCHR --> sys_user: Home informations (address, city, phone, email)
PSPC_Directory --> EntraID: Employment (title)
MyGCHR --> sn_hr_core_profile: Employment (classification, PRI, Empl. ID, first OL, preferred lang.)
EntraID --> sys_user: Employment (title)
sys_user -- sn_hr_core_profile
