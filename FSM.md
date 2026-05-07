```mermaid
classDiagram
namespace Global {
class cmn_location {
AOID/DFRP
Source(sigma_refx)
}
class sys_user {
Source(entra_ID)
}
class core_company {
Source()
}
class sys_user_group {
Source()
}
}
%% ---------
%% catalog architecture
%% ---------
namespace Global_Catalog {
class sc_catalog {
}
class sc_category {
}
class sc_cat_item {
}
}
%% ---------
%% CSM
%% ---------
namespace Global_CSM {
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
