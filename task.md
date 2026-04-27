```mermaid
classDiagram
    class task {
       }
    class sys_user {
       }
    class sys_user_group {
       }
    class cmn_location {
       }
    class sn_hr_le_activity_base {
       }
    class sn_rm_story {
       }
    class sn_hr_sys_user_group {
       }
    class core_company {
       }
    class cmdb_ci {
       }
    class ast_contract {
       }
    class sc_cat_item_delivery_plan {
       }
    class sc_cat_item_delivery_task {
       }
    class sys_esign_configuration {
       }
    class service_offering {
       }
    class cmn_skill {
       }
    class cmn_skill {
       }

task -- sys_user: users
task -- sys_user_group: user's groups
task -- sys_user_group: cmn_location
