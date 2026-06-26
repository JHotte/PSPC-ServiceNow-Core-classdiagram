```mermaid
classDiagram
class rms_employee_dimension {
+RMS_LegalLastName
+RMS_LegalFirstName
+RMS_PreferredLastName
+RMS_PreferredFirstName
+RMS_OfficeEmail
}
class rms_employment_dimention {
+RMS_OrgLevel1
+RMS_EmployeeType
+RMS_InactiveType
}
class ois_employee_dimension {
+OIS_Last_Name
+OIS_First_Name
+OIS_DOB
+OIS_Personnel_File_Number
}
class ois_timestamps_dimension {
+OIS_DateInitiated
+OIS_Date_Completed
+OIS_Date_Granted
+OIS_Date_Expiry
}
class ois_owner {
+OIS_Held_With
+OIS_Org_Type
}
class ois_status {
+OIS_Historical_Status
+OIS_Level_Type
}
class ois_security_clearance_type {
+OIS_Level
+OIS_Level_Code
}
