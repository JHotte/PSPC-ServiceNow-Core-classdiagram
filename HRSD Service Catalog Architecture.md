```mermaid
classDiagram
class Human_Resources_Catalog {
status(active)
sc_catalog
    }
class Inclusivity_safety_and_mental_health {
sc_category
status(active)
    }
class Code_of_conduct_and_declaration_of_conflict_of_interest {
sc_category
status(active)
    }
class Conflict_of_Interest_Declaration_V1.3 {
sc_cat_item_producer
status(active)
    }
class Conflict_of_Interest_Declaration_V2 {
sc_cat_item_producer
status(inactive)
    }
Human_Resources_Catalog -- Inclusivity_safety_and_mental_health
Inclusivity_safety_and_mental_health -- Code_of_conduct_and_declaration_of_conflict_of_interest
Code_of_conduct_and_declaration_of_conflict_of_interest -- Conflict_of_Interest_Declaration_V1.3
Code_of_conduct_and_declaration_of_conflict_of_interest -- Conflict_of_Interest_Declaration_V2
