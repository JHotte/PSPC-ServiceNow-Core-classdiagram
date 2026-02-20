

```mermaid
%% test
classDiagram
    class TBS {
    }
    class Federal_Identity {
+Environment:OpenGov
+Name: Official titles of Government of Canada departments and agencies
-Content()
    }
TBS -- Federal_Identity : owned by
    class Company {
+Environment: ServiceNow
+Name: core_company
    }
Federal_Identity <|-- Company : pulls info from
    class Account {
+Environment: ServiceNow Core
+Label: Account
+System Name: customer_account
    }
Company <|-- Account : extends to
