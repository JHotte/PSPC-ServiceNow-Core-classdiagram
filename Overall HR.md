```mermaid
classDiagram
namespace HRSD {
class sn_hr_core_case
class sn_hr_core_profile {
HR Profiles
}
class sn_hr_core_case_workforce_admin {
Conflict of Interest Declaration
}
class sn_hr_core_case_talent_management {
Departure and Early end of Employment
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
namespace Core {
class task
class sys_user
class cmn_location
class core_country {
Country
class cmn_department
}
}
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
