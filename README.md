## EventConstSubProducer
if(!ecsUseEtaBandsRho_) then the event subtraction proceeds using the default fastjet rho calculation 

if(ecsUseEtaBandsRho_) then the event subtraction proceeds using eta-dependent rho values 

if(ecsUseTaBandsRho_&& ecsUseModulatedRho_) then a flow-modulated rho is also used

EventConstSub producer is based on the SoftKiller template: it reads PF candidates, transforms them into fastjet pseudojets,performs
the subtraction using the ConstituentSubtraction fastjet contrib package functions and then the subtracted list of particles is translated
back to the PF candidate format (makig sure that particles that were removed by the subtraction enter the list of PC candidates with E=0, to satisfy the value map. 
