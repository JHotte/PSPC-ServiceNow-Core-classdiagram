```mermaid
classDiagram
class IT_Service_Catalog {
status(active)
sc_catalog
    }
class Real_Propreties {
status(active)
sc_catalog
    }
class Field_Service_Catalog {
status(active)
sc_catalog
    }
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
class COI_record_producer {
sc_cat_item_producer
status(active)
    }
}
namespace Classification {
class Classification_and_organizational_structure {
sc_category
status(inactive)
    }
class Classification_record_producer{
sc_cat_item_producer
status(inactive)
    }
}
namespace Departure {
class Departure_and_Early_end_of_Employment{
sc_category
status(active)
 }
class Departure_record_producer{
sc_cat_item_producer
status(active)
 }
}
namespace LRD{
class Leave_return_or_departure{
sc_category
status(inactive)
}
class Leave{
sc_category
status(inactive)
}
class Leave_record_producer{
sc_cat_item_producer
status(inactive)
}
class Return{
sc_category
status(inactive)
}
class Return_record_producer{
sc_cat_item_producer
status(inactive)
}
}
namespace PBPP{
class Pay_benefits_and_pension_plan{
sc_category
status(active)
}
class Pay{
sc_category
status(active)
}
class Benefits{
sc_category
status(active)
}
class Pension_plan{
sc_category
status(active)
}
class Pay_record_producer{
sc_cat_item_producer
status(active)
}
class Benefits_record_producer{
sc_cat_item_producer
status(active)
}
class Pension_plan_record_producer{
sc_cat_item_producer
status(active)
}
}
namespace SOBP{
class Staffing_and_On_boarding_of_a_person{
sc_category
status(inactive)
}
class Staffing_record_producer{
sc_category
status(inactive)
}
}
namespace Support_HRB_IT{
class Support_or_access_to_systems_for_HRB_specialists{
sc_category
status(inactive)
}
class Support_HRB_IT_record_producer{
sc_cat_item_producer
status(inactive)
}
}
namespace SLE{
class Second_Language_Evaluation{
sc_category
status(inactive)
}
class SLE_record_producer{
sc_cat_item_producer
status(inactive)
}
}

%% Category
Human_Resources_Catalog -- Inclusivity_safety_and_mental_health
Human_Resources_Catalog -- Classification_and_organizational_structure
Human_Resources_Catalog -- Departure_and_Early_end_of_Employment
Human_Resources_Catalog -- Leave_return_or_departure
Human_Resources_Catalog -- Pay_benefits_and_pension_plan
Human_Resources_Catalog -- Staffing_and_On_boarding_of_a_person
Human_Resources_Catalog -- Support_or_access_to_systems_for_HRB_specialists
Human_Resources_Catalog -- Second_Language_Evaluation

%% Sub_category
Inclusivity_safety_and_mental_health -- Code_of_conduct_and_declaration_of_conflict_of_interest
Inclusivity_safety_and_mental_health -- Diversity_and_inclusion
Inclusivity_safety_and_mental_health -- Health_and_safety_support
Code_of_conduct_and_declaration_of_conflict_of_interest -- COI_record_producer

%% Sub_category
Classification_and_organizational_structure -- Classification_record_producer

%% Sub_category
Departure_and_Early_end_of_Employment -- Departure_record_producer

%% Sub_category
Leave_return_or_departure -- Leave
Leave_return_or_departure -- Return
Leave -- Leave_record_producer
Return -- Return_record_producer

%% Sub_category
Pay_benefits_and_pension_plan -- Pay
Pay_benefits_and_pension_plan -- Benefits
Pay_benefits_and_pension_plan -- Pension_plan
Pay -- Pay_record_producer
Benefits -- Benefits_record_producer
Pension_plan -- Pension_plan_record_producer

%% Sub_category
Staffing_and_On_boarding_of_a_person -- Staffing_record_producer

%% Sub_category
Support_or_access_to_systems_for_HRB_specialists -- Support_HRB_IT_record_producer

%% Sub_category
Second_Language_Evaluation -- SLE_record_producer


