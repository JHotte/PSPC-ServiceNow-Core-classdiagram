```mermaid
classDiagram
direction LR

    class PublicServiceCommission {
        TRST
    }

    class HumanResources {
        MyGCHR
        MyHRRP
        HRSD
    }

    class Finance {
        SAP_SIGMA
    }

    class RGPB {
        Siebel
        Penfax
    }

    class HCMPAB {
        Phoenix
        MyGCPay
        CRM
    }

    class ThirdPartySystems {
        CRA
        CanadaPost
        Unions
        Banks
        Insurance
        ServiceCanada
        ProvincialRevenue
    }

    %% Relationships and Data Flows
    PublicServiceCommission -- MyGCHR : SLE Results
    Finance -- MyGCHR : Financial Delegation
    MyGCHR -- MyHRRP : Data Sync
    MyGCHR -- HRSD : Data Sync
    
    MyGCHR -- Phoenix : HR Data Integration
    RGPB -- Phoenix : Pension/Benefit Data
    
    Phoenix -- MyGCPay : Pay Data View
    Phoenix -- CRM : Case Management
    
    %% Downstream 3rd Party Flows
    Phoenix -- CRA : Taxes (T4/T4A)
    Phoenix -- CanadaPost : T4 Mailing
    Phoenix -- Unions : Deductions
    Phoenix -- Banks : Contributions (Direct Deposit)
    Phoenix -- Insurance : Contributions
    Phoenix -- ServiceCanada : Remuneration Records (ROE)
    Phoenix -- ProvincialRevenue : RL-1 (Quebec)
