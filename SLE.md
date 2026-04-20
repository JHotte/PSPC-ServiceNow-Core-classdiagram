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

class Position {
 +OL_Profile
}

class Preferred_language {
+French
+English
}

class First_official_Language {
+French
+English
}

class Language_Code {
+Cdn French
+English
}

class Requirements {
+Imperative_appointment
+Non-Imperative_appointment
+Acting_appointment
}

SLE_Test_Result --> TestSource : sourced from
TestSource --> Language_tested : tested in
Language_tested --> Test_type : tested for
Test_type --> ResultCode : has
ResultCode --> Requirements : is position is not unilingual
Employee --> Requirements : if appointed
Requirements -->  Position
Employee -->  Preferred_language : has
Employee -->  SLE_Test_Result : might have
Employee -->  First_official_Language
Employee -->  Language_Code
First_official_Language -->  Language_tested : will be tested in other language

