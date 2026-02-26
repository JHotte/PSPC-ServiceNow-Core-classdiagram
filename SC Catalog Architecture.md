

```mermaid
%% TBS   
classDiagram
class sys_metadata {
Application File
}
class sc_catalog {
Catalog
Human Resources Catalog, IT Service Catalog, etc.()
}
class sc_category {
Category
}
sys_metadata <|-- sc_catalog : extend
sc_catalog <|-- sc_category : extend
