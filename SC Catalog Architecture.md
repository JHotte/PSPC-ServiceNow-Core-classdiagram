

```mermaid
classDiagram

%% Service Catalog – Clean High-Level (Containers & Items)

direction LR

class sc_catalog {
  <<table>>
  +Catalogs (ex: HR, IT)
}
class sc_category {
  <<table>>
  +Categories within a catalog
  +Parent for nesting
}

class sc_cat_item {
  <<table>>
  +Catalog Item (base)
}
class sc_cat_item_producer {
  <<extends sc_cat_item>>
  +Record Producer
}
class sc_cat_item_content {
  <<extends sc_cat_item>>
  +Content Item
}
class sc_cat_item_guide {
  <<extends sc_cat_item>>
  +Order Guide
}

class sc_cat_item_category { <<m2m>> }
class sc_cat_item_catalog { <<m2m>> }

sc_cat_item <|-- sc_cat_item_producer
sc_cat_item <|-- sc_cat_item_content
sc_cat_item <|-- sc_cat_item_guide

sc_catalog "1" o-- "many" sc_category
sc_category "1" o-- "many" sc_cat_item_category
sc_cat_item_category "many" o-- "1" sc_cat_item

sc_catalog "1" o-- "many" sc_cat_item_catalog
sc_cat_item_catalog "many" o-- "1" sc_cat_item
