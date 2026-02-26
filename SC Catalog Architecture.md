

```mermaid
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
Hire a person or extend employment, Support for staffing specialists()
}
class sc_cat_item {
Catalog Item
}
class sc_cat_item_producer {
Record Producer
Name, Short description ()
}
sys_metadata <|-- sc_catalog : extend
sc_catalog <|-- sc_category : extend
sc_category <|-- sc_cat_item : extend
sc_cat_item <|-- sc_cat_item_producer : extend
