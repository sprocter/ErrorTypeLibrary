Architectural Documentation
===========================

Assumptions
-----------

### Overall

1. Unless otherwise noted, semantics are identical to latest version of EMV2 standard

### Apps

1. Apps have both physiological and control action ports
2. Both ```TransientServiceOmission``` and ```BoundedOmissionInterval``` are used because apps with averaging algorithms may require the distinction. A service is considered to have recovered from a ```TransientServiceOmission``` when service items resume transmission, but a service requires some number (*k*) of valid service items before having recovered from a ```BoundedOmissionInterval```. An app with an averaging algorithm that requires 10 subsequent values for some parameter or control action will not have recovered if, for example, seven values are transmitted before the service drops again.
3. Both out of range and out of bounds errors are included because we expect that many apps will have the application domain function to calculate out of bounds errors. For example, an app may expect some physiological parameter that is a percentage, so -1% and 101% would be out of range, but it may also expect that it's not possible for drops of more than 10% in a minute, so a value of 50% after a previous reading of 90% would be out of bounds.
4. We do not expect apps to compensate differently for values that are too high or too low (according to either range or bounds calculations) so we include only one type of error.