```mermaid
classDiagram
class sys_user {
label:user
+status:active
}
class cmn_building {
label:Building
+status:active
}
class core_company {
label:Company
+status:active
}
%% ----------
Linkages
%% ----------
sys_user -- cmn_building
sys_user -- core_company
