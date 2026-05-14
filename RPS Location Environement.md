```mermaid
classDiagram
namespace TBS {
class DFRP {
}
}
namespace SIGMA {
class ReFX {
AO_ID(id)
Side_ID(id)
Building_AO_ID(id)
}
}
namespace EDW {
class EDW_Building_Location {
EDW_RPUID(id)
}
}
namespace NSCC {
class NMMS {
}
}
namespace ServiceNow_Core_DEV {
class cmn_location_DEV {
}
}
namespace ServiceNow_Core_PROD {
class cmn_location_PROD {
}
}
namespace ServiceNow_EAM {
class alum_site {
DFRP_alig: Site
Sigma align:
}
class alm_facility {
DFRP_alig: Building/Structure
}
class alm_floor {
}
class alm_space {
}
class alm_asset {
}
}
%% ----------
%% Linkages
%% ----------
alum_site -- alm_facility
alm_facility -- alm_floor
alm_floor -- alm_space
alm_space -- alm_asset
ReFX -- EDW_Building_Location
EDW_Building_Location -- cmn_location_DEV
DFRP -- ReFX: DFRP proprety number
