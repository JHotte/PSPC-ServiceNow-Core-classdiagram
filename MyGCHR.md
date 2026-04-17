```mermaid
classDiagram
namespace Public_Service_Commission {
    class TRST {
            } }
namespace Human_Resources {
    class MyGCHR {
            }
class MyHRRP {
            }
class HRSD {
            } 
}
namespace Finances {
    class SIGMA {
            } }
TRST -- MyGCHR: SLE results
SIGMA -- MyGCHR: Financial delegation
