```mermaid
classDiagram
%% Core CMDB
namespace CMDB {
class cmdb_ci {
Business Applications and Solutions (ITSM catalog)
}
class cmdb
}
%% Relationship - CMDB
cmdb -- cmdb_ci : extend
