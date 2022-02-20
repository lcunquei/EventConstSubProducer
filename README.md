## EventConstSubProducer
if(!ecsUseEtaBandsRho_) then the event subtraction proceeds using the default fastjet rho calculation 

if(ecsUseEtaBandsRho_) then the event subtraction proceeds using eta-dependent rho values 

if(ecsUseTaBandsRho_&& ecsUseModulatedRho_) then a flow-modulated rho is also used

EventConstSub producer is based on the SoftKiller template: it reads PF candidates, transforms them into fastjet pseudojets,performs
the subtraction using the ConstituentSubtraction fastjet contrib package functions and then the subtracted list of particles is translated
back to the PF candidate format (makig sure that particles that were removed by the subtraction enter the list of PC candidates with E=0, to satisfy the value map)

In order to modulate rho in terms of eta ranges and flow, I have to first distribute ghosts uniformly in the acceptance and then modify
their 4-vectors according to their position, to finally call the subtraction using the list of input particles and list of modified ghosts. 

The procedure is similar to what is done in RecoJets/JetProducers/plugins/CSJetProducer.cc, with the difference that in that case the subtraction is done to a jet and uniformly distributed ghosts already exist as consituents of the jet from the clustersequence. 
