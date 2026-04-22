```mermaid
classDiagram
class Human_Resources_Catalog {
status(active)
sc_catalog
    }
namespace COI {
class Inclusivity_safety_and_mental_health {
sc_category
status(active)
    }
class Code_of_conduct_and_declaration_of_conflict_of_interest {
sc_category
status(active)
    }
class Diversity_and_inclusion {
sc_category
status(inactive)
    }
class Health_and_safety_support {
sc_category
status(inactive)
    }
class Conflict_of_Interest_Declaration_V1.3 {
sc_cat_item_producer
status(active)
    }
class Conflict_of_Interest_Declaration_V2 {
sc_cat_item_producer
status(inactive)
    }
}
Human_Resources_Catalog -- Inclusivity_safety_and_mental_health
Inclusivity_safety_and_mental_health -- Code_of_conduct_and_declaration_of_conflict_of_interest
Inclusivity_safety_and_mental_health -- Diversity_and_inclusion
Inclusivity_safety_and_mental_health -- Health_and_safety_support
Code_of_conduct_and_declaration_of_conflict_of_interest -- Conflict_of_Interest_Declaration_V1.3
Code_of_conduct_and_declaration_of_conflict_of_interest -- Conflict_of_Interest_Declaration_V2
