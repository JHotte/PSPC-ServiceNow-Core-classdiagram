```mermaid
classDiagram
direction LR
class Employee {
        +employee_id
        +first_official_language
        +is_bilingual_bonus_eligible
    }

class SLE_Test_Result {
        +test_type
        +result_code
        +evaluation_date
        +expiration_date
    }

class Language_tested {
        French
        English
            }
class Test_type {
        Reading
        Writing
        Oral
            }
class ResultCode {
        X : Fail
        A : Beginner
        B : Intermediate
        C : Advanced
        E : Exempt
    }
    
class TestSource {
    Public Service Commission
    Departmental
    Note(Not in MyGCHR)
}

SLE_Test_Result --> TestSource : sourced_from
SLE_Test_Result --> Test_type : sourced_from
Employee --> SLE_Test_Result : has
SLE_Test_Result --> Language_tested : evaluated_in
SLE_Test_Result --> ResultCode : yields
