## EventConstSubProducer
if(!ecsUseEtaBandsRho_) the event subtraction proceeds using the default fastjet rho calculation 

if(ecsUseEtaBandsRho_) the event subtraction proceeds using eta-dependent rho values 

if(ecsUseTaBandsRho_&& ecsUseModulatedRho_) in addition, a flow-modulated rho is used

EventConstSub producer is based on the SoftKiller template: it reads PF candidates, transforms them into fastjet pseudojets,performs
the subtraction using the ConstituentSubtraction fastjet contrib package functions and then the subtracted list of particles is translated
back to the PF candidate format (makig sure that particles that were removed by the subtraction enter the list of PC candidates with E=0, to satisfy the value map)

In order to modulate rho in terms of eta ranges and flow, I have to first distribute ghosts uniformly in the acceptance and then modify
their 4-vectors according to their position, to finally call the subtraction using the list of input particles and list of modified ghosts. 

The procedure is similar to what is done in RecoJets/JetProducers/plugins/CSJetProducer.cc, with the difference that in that case the subtraction is done to a jet and uniformly distributed ghosts already exist as consituents of the jet from the clustersequence. 

 In the jet-by-jet case, the maximum distance at which you combine particles and ghosts is set to the jet radius and ghosts are only placed within the jet. The momentum of the ghosts adds up to rho*jet_area. Naturally, particles at the border of the jet are less subtracted than particles closer to the jet axis so this leads to an enhanced yield of particles and combinatorial prongs at the edges. The pT of the jet is subtracted exactly by rho*jet_area.
 
 In the event-wise case, ghosts are placed all over the phase space and the edge problem disappeares. Then one needs to decide up to which distance to combine particles and ghosts. Default value Rmax=1 leads to oversubtraction because more pT than just rho*jet_area is subtracted. While smaller Rmax lead to an undercorrection of the jet pT. 

 
 In ALICE we found that Rmax~025 did not bias the jet pT for R=0.2 and R=0.4 jets. The optimal value needs to be tested and might not be the same for all jet R. 
 
 
 ## Testing it
 
 In order to test it, I downloaded JetToolBox: https://twiki.cern.ch/twiki/bin/viewauth/CMS/JetToolbox
 and extended the configuration file to have this new ECS producer and jets. 
 
 
## Performance plots
 
 
  
 
 
 
 
