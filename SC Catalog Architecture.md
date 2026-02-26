

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
}
class sc_cat_item_category {
Category + item
}
class sc_cat_item_catalog {
Catalog + items
}
}
%% Core Arborescence
sys_metadata <|-- sc_catalog : extend
sc_catalog <|-- sc_category : extend
sc_category <|-- sc_cat_item : extend
sc_cat_item <|-- sc_cat_item_producer : extend
sc_cat_item_category -- sc_cat_item
sc_cat_item_category -- sc_category
sc_cat_item_catalog -- sc_cat_item
sc_cat_item_catalog -- sc_catalog

