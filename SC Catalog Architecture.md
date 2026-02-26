

```mermaid
classDiagram
%% ServiceNow
namespace ServiceNow {
class sys_metadata {
Application File
}
class sc_catalog {
Catalog
}
class sc_category {
Category
}
class sc_cat_item {
Catalog Item
}
class sc_cat_item_producer {
Record Producer
Name, Short description ()
}
}
%% HRSD
namespace HRSD {
class Human Resources Catalog
class Staffing and On-boarding of a person
}
%% ITSM
namespace ITSM {
class IT Service Catalog
}
%% RPS
namespace FSM {
class Real Properties
}
%% Core Arborescence
sys_metadata <|-- sc_catalog : extend
sc_catalog <|-- sc_category : extend
sc_category <|-- sc_cat_item : extend
sc_cat_item <|-- sc_cat_item_producer : extend
%% HRSD Arborescence
Human Resources Catalog -- sc_catalog
Human Resources Catalog <|-- Staffing and On-boarding of a person
Staffing and On-boarding of a person -- sc_category
%% FSM Arborescence
Real Properties -- sc_catalog
%% ITSM Arborescence
IT Service Catalog -- sc_catalog
