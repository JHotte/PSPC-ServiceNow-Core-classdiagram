```mermaid
classDiagram
direction LR

    class MyGCHR {
        +PRI
        +position_number
        +classification_level
        +official_language_profile
        +home_mailing_address
        +leave_balances
    }

    class Phoenix {
        +gross_net_pay
        +pay_line_items
        +statutory_deductions
        +pension_benefit_premiums
        +direct_deposit_details
        +tax_province
    }

    class MyGCPay {
        <<Visualization>>
        +view_hr_profile()
        +view_pay_stubs()
        +track_pay_cases()
        +view_tax_slips()
    }

    MyGCHR -- MyGCPay : Syncs Profile & Leave
    Phoenix -- MyGCPay : Syncs Pay & Deduction Data
    MyGCHR -- Phoenix : Triggers Pay Actions
