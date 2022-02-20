import FWCore.ParameterSet.Config as cms


EventConstSub = cms.EDProducer("EventConstSubProducer",
                       PFCandidates       = cms.InputTag('particleFlow'),
                               ecsRho_EtaMax = cms.double( 2.4 ),
                               ecsrParam = cms.double( 0.4 ),
                               ecsrMax = cms.double(0.25),
                               ecsalpha = cms.double(0),
                               ecsghostarea = cms.double(0.005),
                               ecsUseModulatedRho = cms.bool(False),
                               ecsUseEtaBandsRho = cms.bool(True),
                               etaMap=cms.InputTag('hiFJRhoProducer','mapEtaEdges'),
                               rho=cms.InputTag('hiFJRhoProducer','mapToRho'),
                               rhom=cms.InputTag('hiFJRhoProducer','mapToRhoM'),
                               minFlowChi2Prob=cms.double(0.05),
                               maxFlowChi2Prob=cms.double(0.95),
                               rhoFlowFitParams=cms.InputTag('hiFJRhoFlowModulationProducer','rhoFlowFitParams')
                        
)
