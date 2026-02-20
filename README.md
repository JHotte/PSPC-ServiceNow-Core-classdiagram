

```mermaid
%% TBS   
classDiagram
    class TBS {
    }
    class Government of Canada Organization Names and Codes - Concordance Data {
+Environment:Open Government​ Dataset
    }
TBS -- Government of Canada Organization Names and Codes - Concordance Data : owned by
    class Government of Canada Organization Names and Codes - Organization Information {
+Environment: Open Governement Dataset
    }
TBS -- Government of Canada Organization Names and Codes - Organization Information : owned by
    class Company {
+Environment: ServiceNow Core
+System Name: core_company
    }
Government of Canada Organization Names and Codes - Organization Information <|-- Company : pulls infom from
    class Account {
+Environment: ServiceNow Core
+Label: Account
+System Name: customer_account
    }
Government of Canada Organization Names and Codes - Concordance Data <|-- Account : pulls info from
Company -- Account
