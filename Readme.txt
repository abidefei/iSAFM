Dear reviewers and readers:

Requirements
The following are needed for running the basic setup
•	Atelier B, Version 4.5 or later, Windows OS (We modelled it on the Windows version)

Explanation
There a difference between this model and the model in the paper mentioned:

For ease of understanding, the paper describes the upClosing/downClosing in the model as upArriving/downArriving.

The 'inv1' described in the 4.4.2 section of the paper is shown below:
   inv1 : (ran(trainPosition_r) /\ {upClosing} /={} & ran(command_r) /\ {upKeepgoing} /={}  
           => barrierState = BARRIERS * {closed} & rlcState = clear & trainMA(upTrain) = upMA) &
          (ran(trainPosition_r) /\ {downClosing} /={} & ran(command_r) /\ {downKeepgoing} /={}
           => barrierState = BARRIERS * {closed} & rlcState = clear & trainMA(downTrain) = downMA)

The 'inv1' described in this model is shown below:
    (ran(trainPosition_r) /\ {upClosing} /= {} & ran(command_r) /\ {upKeepgoing} /= {} =>
    barrierState(enBarrier) = closed & barrierState(exBarrier) = closed & rlcState = clear & ran(trainMA) /\ {upMA} /= {}) &
    (ran(trainPosition_r) /\ {downClosing} /= {} & ran(command_r) /\ {downKeepgoing} /= {} =>
    barrierState(enBarrier) = closed & barrierState(exBarrier) = closed & rlcState = clear & ran(trainMA) /\ {downMA} /= {})

So, the difference is that the 'train(upTrain) = upMA' is altered for ran(trainMA) /\ {upMA} /= {} and 'train(downTrain) = downMA' is altered for ran(trainMA) /\ {downMA} /= {}

These two changes do not modify the contents or model space that the invariants need to check. Just the more appropriate descriptions are used to assist the proof works in the currrent structure of the model.  We can prove that the decriptions ('ran(trainMA) /\ {upMA} /= {}' for 'train(upTrain) = upMA'  and 'ran(trainMA) /\ {downMA} /= {}' for 'train(downTrain) = downMA') are equivalent based on the invariants are defined in the machine trainMoveAuthority.

2023-09-09
