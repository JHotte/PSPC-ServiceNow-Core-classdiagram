```mermaid
classDiagram
class rms_employee_dimension {
+LegalLastName
+LegalFirstName
+PreferredLastName
+PreferredFirstName
+OfficeEmail
}
class rms_employment_dimention {
+OrgLevel1
+EmployeeType
+InactiveType
}
class ois_employee_dimension {
+Last_Name
+First_Name
+DOB
+Personnel_File_Number
}
class ois_timestamps {
+DateInitiated
+Date_Completed
+Date_Granted
+Date_Expiry
}
class ois_holding_possession {
+Held_With
}
