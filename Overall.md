```mermaid
classDiagram
namespace PSPC_FB {
    class SIGMA {
    }
    class EODS {
    }
}
namespace PSPC_HR {
    class MyGCHR {
    }
    class ServiceNow_HRSD {
    }
    class ServiceDeskplus {
    }
}
namespace PSPC_DSB {
class ServiceNow_Core {
    }
class EntraID {
    }
class AD {
    }
class PSPCD {
    }
}
namespace SSC {
class SM9 {
}
class GC_Directory {
}
}
namespace PSPC_RPS {
class RPMS {
}
}
namespace PSPC_DOB {
class OLISS {
}
}
%% Links %%%
EntraID -- ServiceNow_Core: "Application Registry - Microsoft Entra ID Spoke OAuth"
PSPCD -- AD
AD -- EntraID
MyGCHR -- ServiceNow_Core
ServiceNow_Core -- ServiceNow_HRSD
SIGMA -- ServiceNow_Core: "Locations"
SM9 -- AD
