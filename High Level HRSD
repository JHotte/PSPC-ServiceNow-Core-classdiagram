```mermaid
classDiagram

    %% ══════════════════════════════════════════════════════════
    %% DIAGRAM 1 — CORE TABLES
    %% Scope: task → sn_hr_core_case → HR extend tables
    %% Excludes: u_gc127_ custom fields (see COE-specific diagrams)
    %% ══════════════════════════════════════════════════════════

    %% ── TASK (ServiceNow base) ──────────────────────────────
    class task {
        +📋 Task (task)
        +🎯 Base table for all work items in ServiceNow
        ---
        +number: string
        +short_description: string
        +description: string
        +state: integer
        +priority: integer
        +urgency: integer
        +impact: integer
        +contact_type: string
        +opened_at: glide_date_time
        +opened_by: reference
        +closed_at: glide_date_time
        +closed_by: reference
        +close_notes: string
        +assigned_to: reference
        +assignment_group: reference
        +company: reference
        +location: reference
        +parent: reference
        +approval: string
        +approval_history: journal
        +approval_set: glide_date_time
        +due_date: glide_date_time
        +made_sla: boolean
        +sla_due: due_date
        +watch_list: glide_list
        +work_notes: journal_input
        +comments: journal_input
        +sys_class_name: sys_class_name
        +sys_id: GUID
        +sys_created_on: glide_date_time
        +sys_created_by: string
        +sys_updated_on: glide_date_time
        +sys_updated_by: string
    }

    %% ── HR CASE (HRSD core) ─────────────────────────────────
    class sn_hr_core_case {
        +📋 HR Case (sn_hr_core_case)
        +🎯 Core HR service delivery case — extends task
        ---
        +opened_for: reference
        +subject_person: reference
        +subject_person_hr_profile: reference
        +subject_person_job: reference
        +hr_service: reference
        +hr_profile: reference
        +department: reference
        +topic_category: reference
        +topic_detail: reference
        +stage: reference
        +source: reference
        +template: reference
        +details: translated_html
        +rich_description: html
        +fulfillment_instructions: translated_html
        +resolution_requires: Choice
        +sla: percent_complete
        +sla_breached: boolean
        +sla_suspended: boolean
        +sla_suspended_on: glide_date_time
        +actual_resolution_time: decimal
        +ettr: decimal
        +case_reassignment_count: integer
        +collaborators: glide_list
        +case_support_team: glide_list
        +bulk_case_request: reference
        +initiated_from: reference
        +transferred_from: reference
        +transferred_to: reference
        +document_template: reference
        +draft_document: reference
        +generated_document: reference
        +pdf_template: reference
        +le_progress: le_progress
        +workflow: reference
        +sys_id: GUID
    }

    %% ── PAYROLL EXTEND ──────────────────────────────────────
    class sn_hr_core_case_payroll {
        +📋 Payroll Case (sn_hr_core_case_payroll)
        +🎯 Extends HR Case for Pay COE — adds payroll-specific fields
        ---
        +pay_discrepancy_type: string
        +business_justification: string
        +direct_deposit: reference
        +account_type: string
        +account_number: string
        +account_nickname: string
        +routing_number: string
        +deposit_type: string
        +deposit_amount: currency
        +deposit_percent: decimal
        +sys_id: GUID
    }

    %% ── BENEFITS EXTEND ─────────────────────────────────────
    class sn_hr_core_case_benefits {
        +📋 Benefits Case (sn_hr_core_case_benefits)
        +🎯 Extends HR Case for Benefits COE — no OOB fields beyond sys_id
        ---
        +sys_id: GUID
    }

    %% ── WORKFORCE ADMIN EXTEND ──────────────────────────────
    class sn_hr_core_case_workforce_admin {
        +📋 Workforce Admin Case (sn_hr_core_case_workforce_admin)
        +🎯 Extends HR Case for WFA COE — staffing, classification, relocation
        ---
        +change_date: glide_date
        +office_location: reference
        +relocation_date: glide_date
        +relocation_address: multi_two_lines
        +relocation_city: string
        +relocation_state: string
        +relocation_country: reference
        +relocation_zip: string
        +relocation_reason: string
        +recipient_email: email
        +work_visa_required: boolean
        +sys_id: GUID
    }

    %% ── TALENT MANAGEMENT EXTEND ────────────────────────────
    class sn_hr_core_case_talent_management {
        +📋 Talent Management Case (sn_hr_core_case_talent_management)
        +🎯 Extends HR Case for departures, onboarding, background checks
        ---
        +business_justification: string
        +background_check_status: string
        +background_check_result: string
        +background_check_percentage_complete: string
        +background_check_package: reference
        +drug_screening_status: string
        +drug_screening_result: string
        +country_travelling_to: reference
        +trip_duration: string
        +visa_category: reference
        +sys_id: GUID
    }

    %% ── LIFECYCLE EVENT CASE ────────────────────────────────
    class sn_hr_le_case {
        +📋 Lifecycle Event Case (sn_hr_le_case)
        +🎯 Extends HR Case for lifecycle events — onboarding, LWOP, transfers
        ---
        +needs_work_visa: boolean
        +needs_transfer_work_visa: boolean
        +needs_relocation_assistance: boolean
        +needs_corporate_credit_card: boolean
        +sys_id: GUID
    }

    %% ══════════════════════════════════════════════════════════
    %% RELATIONSHIPS
    %% ══════════════════════════════════════════════════════════

    task <|-- sn_hr_core_case : extends
    sn_hr_core_case <|-- sn_hr_core_case_payroll : extends
    sn_hr_core_case <|-- sn_hr_core_case_benefits : extends
    sn_hr_core_case <|-- sn_hr_core_case_workforce_admin : extends
    sn_hr_core_case <|-- sn_hr_core_case_talent_management : extends
    sn_hr_core_case <|-- sn_hr_le_case : extends
