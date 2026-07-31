```mermaid
flowchart TD
%% PART 1: INITIATION
    F1["Requester's name<br>(opened_for)"]
    F2["Other people who can view and track the requester<br>(other_people_who_can_view_and_track_the_request)"]
    F3["Name of the manager with delegated financial authority-Required<br>(u_gc127_delegated_mgr)"]
    F4["Financial Delegation-Section34<br>(financial_delegation_1)"]
    F5["Position number of manager with delegated financial authority–Required<br>(position_number_of_manager)"]
    F6["Are you requesting a change for more than one position?–Required<br>(are_you_requesting_a_change_for_more_than_one_position)"]
    F7["Position number–Required<br>(u_gc127_position)"]
    F8["This position is vacant–Required<br>(u_gc127_position)"]
    F9
%% PART 1: INITIATION (LINKAGE)
Modify_a_position --> F1
F1 --> F2
F2 --> F3
F3 --> F4
F4 --> F5
F5 --> F6
F6 -- No --> F7
F6 -- Yes --> F8
