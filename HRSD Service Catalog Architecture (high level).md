```mermaid
classDiagram
class Catalog {
ServiceNow_Catalog_Container
    sc_catalog
 }
class IT_Service_Catalog {
sc_catalog
status_active
sc_catalog
    }
class Real_Propreties {
sc_catalog
status_active
sc_catalog
    }
class Field_Service_Catalog {
sc_catalog
status_active
sc_catalog
    }
class Human_Resources_Catalog {
sc_catalog
status_active
sc_catalog
    }
namespace COI {
class Inclusivity_safety_and_mental_health {
sc_category
status_active
    }
class Code_of_conduct_and_declaration_of_conflict_of_interest {
sc_category
status_active
    }
class Diversity_and_inclusion {
sc_category
status_inactive
    }
class Health_and_safety_support {
sc_category
status_inactive
    }
class COI_record_producer {
sc_cat_item_producer
status_active
Conflict_of_interest_V_1_3(rp)
Conflict_of_interest_V_2_0(rp)

    }
}
namespace Classification {
class Classification_and_organizational_structure {
sc_category
status_inactive
    }
class Classification_record_producer{
sc_cat_item_producer
status_inactive
Create_or_abolish_a_position(rp)
Update_a_position(rp)
    }
}
namespace DEE {
class Departure_and_Early_end_of_Employment{
sc_category
status_active
 }
class Departure_record_producer{
sc_cat_item_producer
status_active
End of employment(rp)
Transfer_out_to_another_federal_organization(rp)
Non-renewal_of_a_term_employment(rp)
Early_end_of_a_temporary_employment(rp)
 }
}
namespace LRD{
class Leave_return_or_departure{
sc_category
status_inactive
}
class Leave{
sc_category
status_inactive
}
class Leave_record_producer{
sc_cat_item_producer
status_inactive
}
class Return{
sc_category
status_inactive
}
class Return_record_producer{
sc_cat_item_producer
status_inactive
}
class Departure{
sc_category
status_inactive
}
class Departure_record_producer{
sc_cat_item_producer
status_inactive
}
}
namespace PBPP{
class Pay_benefits_and_pension_plan{
sc_category
status_active
}
class Pay{
sc_category
status_active
}
class Benefits{
sc_category
status_active
}
class Pension_plan{
sc_category
status_active
}
class Pay_record_producer{
sc_cat_item_producer
status_active
}
class Benefits_record_producer{
sc_cat_item_producer
status_active
}
class Pension_plan_record_producer{
sc_cat_item_producer
status_active
}
}
namespace SOBP{
class Staffing_and_On_boarding_of_a_person{
sc_category
status_inactive
}
class Staffing_record_producer{
sc_cat_item_producer
status_inactive
}
}
namespace Support_HRB_IT{
class Support_or_access_to_systems_for_HRB_specialists{
sc_category
status_inactive
}

class MyGCHR_and_Phoenix{
sc_category
status_inactive
}
class MyGCHR_and_Phoenix_record_producer{
sc_cat_item_producer
status_inactive
Modify employment or personal information(rp)
Platforms access issue(rp)
Support with Leave, overtime, or compensatory time(rp)
Support with Employee OR Manager Self-service(rp)
}
}
namespace SLE{
class Second_Language_Evaluation{
sc_category
status_inactive
}
class SLE_record_producer{
sc_cat_item_producer
status_inactive
}
}
namespace Support_HR{
class Support_for_staffing_specialists{
sc_category
status_inactive
}
class Support_HR_record_producer{
sc_cat_item_producer
status_inactive
}
}

%% Catalog
Catalog -- IT_Service_Catalog
Catalog -- Real_Properties_Catalog
Catalog -- Field_Service_Catalog
Catalog -- Human_Resources_Catalog

%% Category
Human_Resources_Catalog -- Inclusivity_safety_and_mental_health
Human_Resources_Catalog -- Classification_and_organizational_structure
Human_Resources_Catalog -- Departure_and_Early_end_of_Employment
Human_Resources_Catalog -- Leave_return_or_departure
Human_Resources_Catalog -- Pay_benefits_and_pension_plan
Human_Resources_Catalog -- Staffing_and_On_boarding_of_a_person
Human_Resources_Catalog -- Support_or_access_to_systems_for_HRB_specialists
Human_Resources_Catalog -- Second_Language_Evaluation
Human_Resources_Catalog -- Support_for_staffing_specialists

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
Leave_return_or_departure -- Departure
Leave -- Leave_record_producer
Return -- Return_record_producer
Departure -- Departure_record_producer

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
Support_or_access_to_systems_for_HRB_specialists -- MyGCHR_and_Phoenix

%% Sub_category
Second_Language_Evaluation -- SLE_record_producer

%% Sub_category
Support_for_staffing_specialists -- Support_HR_record_producer
MyGCHR_and_Phoenix -- MyGCHR_and_Phoenix_record_producer


