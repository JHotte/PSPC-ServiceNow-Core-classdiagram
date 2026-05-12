```mermaid
classDiagram
class sys_user {
label:user
+status:active
}
class building {
label:Building
+status:inactive
}
%% ----------
Linkages
%% ----------
sys_user -- building
