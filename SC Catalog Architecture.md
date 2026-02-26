

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
Catalogs/Category/Name()
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
class sys_scope {
Application
}
class sys_user {
User
}
class sc_cat_item_content {
Content Item
}
}
class Branch
class BranchCategory
class FormIntake
%% Core Arborescence
sys_metadata <|-- sc_catalog : extend
sc_catalog <|-- sc_category : extend
sc_category <|-- sc_cat_item : extend
sc_cat_item -- sc_cat_item_producer : "Published item"
sc_cat_item .. sys_metadata
sc_cat_item_category -- sc_cat_item
sc_cat_item_category -- sc_category
sc_cat_item_catalog -- sc_cat_item
sc_cat_item_catalog -- sc_catalog
sc_cat_item_content -- sc_cat_item : "Published item"
sys_scope -- sc_catalog : "Application"
sc_catalog -- sys_user : "Manager"
BranchCategory .. sc_category
Branch .. sc_catalog
FormIntake .. sc_cat_item_producer
