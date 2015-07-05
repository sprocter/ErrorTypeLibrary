Architectural Documentation
===========================

Assumptions
-----------

### Overall

1. Unless otherwise noted, semantics are identical to latest version of EMV2 standard

### Apps

1. Apps have both physiological and control action ports
2. Both ```TransientServiceOmission``` and ```BoundedOmissionInterval``` are used because apps with averaging algorithms may require the distinction. A service is considered to have recovered from a ```TransientServiceOmission``` when service items resume transmission, but a service requires some number (*k*) of valid service items before having recovered from a ```BoundedOmissionInterval```. An app with an averaging algorithm that requires 10 subsequent values for some parameter or control action will not have recovered if, for example, seven values are transmitted before the service drops again.