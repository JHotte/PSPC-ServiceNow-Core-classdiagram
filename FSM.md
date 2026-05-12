```mermaid
classDiagram
%% ---------
%% User
%% ---------
namespace Global_User {
class sys_user_group {
Source()
}
class sys_user {
Source(entra_ID)
}
}
namespace Global_Core {
class cmn_location {
AOID/DFRP
Source(sigma_refx)
}
class core_company {
Source()
}
}
%% ---------
%% catalog architecture
%% ---------
namespace Global_Catalog {
class sc_catalog {
Label: Catalog
Real Properties (catalog)
Field Service Catalog (catalog)

}
class sc_category {
Label: Category
}
class sc_cat_item {
}
}
%% ---------
%% FSM
%% ---------
namespace Global_FSM {
class wm_order {
Primary Record
}
}

%% ---------
%% linkages
%% ---------

sys_user -- cmn_location: contact
cmn_location -- core_company: company
sys_user -- sys_user_group: manager/default assignee
%% ---------
%% catalog linkages
%% ---------
sc_catalog -- sc_category: catalog
sc_category -- sc_cat_item: catalog
