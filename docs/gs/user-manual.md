# User Manual 


We have two main types of chips (production and development) and two types of procedures (traditional and pick&place) for stapling. <br>

While production chips have the goal of being delivered to the measurement team, the NA team is in charge of designing development chips to test new device designs (for example, different types of device geometries) or new assembly recipes (annealing recipes, different materials, high density of devices on a single chip…). 

Currently, most prod chips are double quantum dots (DQDs), i.e. they have 5 gates, and cavity test chips, for quality factor and frequency determination. C12 designs in house their prod chips. Development chips are instead outsourced to different collaborators (ANL, for example), and are what we call single quantum dots (SQDs), i.e. they have typically 1 or 3 gates. 

Note that designs can actually vary a lot between different chips (even when coming from the same wafer!), so always doublecheck!
We have two main procedures to actually complete a nanoassembly event:

   - (i) Traditional stapling
   - (ii) Pick&Place (P&P) stapling

!!! note "Note"
    P&P stapling is something that is currently (July 2025) becoming more routine within NA. 

!!! info "Main Difference"

    The main difference between 
    (i) traditional stapling and (ii) P&P stapling is that  (i) requires large trenches at the sides of the  devices to accomodate the full width of the CAD, while   (ii) requires only smaller pits to accomodate the two thines of the fork. Because of this, theoretically P&P can be performed on all devices (trenches or pits), but traditional stapling is only compatible with devices with trenches. 

While in traditional stapling the CAD is mounted on the SWAN motors and directly used for stapling, in P&P we have an intermediate step: the CAD is mounted at the side, while we move a fork to pick up the CNT from the CAD and staple it onto the chip.

!!! warning "Why not P&P for all production chips?"
    Currently, we don’t do P&P on production chips because  we don’t have a physical place to secure the CAD in  the assembler chamber (just because we are waiting for   a mechanical piece, it should be sorted soon!). 
    We also have the issue that at the moment P&P in not    compatible at all (neither for prod nor for dev) with  full vacuum transfer.
### Preparation of samples before insertion in A1

Tergeo cleaning of chips (usually 25 W for 10 mins), but the recipe might be shortened following the cleaning tests of July 2025 
!!! danger "Ozone cleaning"
    O2 cleaning - possibly dangerous for cavity <br>
    H2 cleaning - should not be aggressive on the chip,     but issues with H2 exhaust

### Stapling tricks
**Trick 1:** stapling bundles is a good way to check whether the device works or not, if the detaction of SW-CNTs is being dodgy. This is because bundles and multiwalls have several more current channels, and so currents can be significantly (orders of magnitude) higher.
Traditional stapling on chips with trenches - not vacuum transfer

### Preparation
Mount QCage (open) on the transfer arm by screwing it on the appropriate mount (there are different mounts for different sampleholders/functions). The whole QCage needs to be mounted on an appropriate rotator device (we have several with different angle corrections) that will correct the relative angle between CAD and chip to increase the chance of good transfer (the support changes based on whether the chosen CNT is left or right of the center of the CAD; once you have chosen a side of the CAD, you need to stick to it cause you won’t be able to assemble CNTs from the other side without crashing the cantilevers into the CAD).

## Preparation of samples before insertion in A1

1. Tergeo cleaning of chips (usually 25 W for 10 mins), but the recipe might be shortened following the cleaning tests of July 2025 
2. Ozone cleaning
3. O2 cleaning - possibly dangerous for cavity
4. H2 cleaning - should not be aggressive on the chip, but issues with H2 exhaust

## Stapling tricks

**Trick 1:** stapling bundles is a good way to check whether the device works or not, if the detaction of SW-CNTs is being dodgy. This is because bundles and multiwalls have several more current channels, and so currents can be significantly (orders of magnitude) higher.

# Traditional stapling on chips with trenches - not vacuum transfer

### **Preparation**

1. Mount QCage (open) on the transfer arm by screwing it on the appropriate mount (there are different mounts for different sampleholders/functions). The whole QCage needs to be mounted on an appropriate rotator device (we have several with different angle corrections) that will correct the relative angle between CAD and chip to increase the chance of good transfer (the support changes based on whether the chosen CNT is left or right of the center of the CAD; once you have chosen a side of the CAD, you need to stick to it cause you won’t be able to assemble CNTs from the other side without crashing the cantilevers into the CAD).
2. Check all channels in Matrix are grounded from software 
3. Attach connectors (Nano-Ds) at the back of the QCage after removing the shorting caps from it. Each connector has 25 lines. There is only one way to insert the connectors, so it should not possible to invert them.
4. Mount CAD on the SWAN (by screwing the M6 Allen-key screw)
5. Check that the QCage can move freely on the manipulator
6. Check that the SWAN can move in all directions
7. Unlock the lid robot from the side of the cleanroom, bring the lid over the assembler and close the assembler by pressing the down arrow on the robot controller
8. Undo the three clamps on the lid, remove the rebot and lock it at the side of the cleanroom
9. Start pumping the assembler down. We have a rough pump (Back) prepumping the turbo pump (Turbo) and we have a rough pump (Rough) dedicated to create the low vacuum in the assembler. Pumps are always all on, we just close valves between Rough and assembler and between Turbo and assembler, depending on the operation. 
    1. From the jbox (controlling all valves on the system), switch rough on (back should  be on, with gate off)
    2. When pressure reaches 10^-1 hPa, switch the gate to on. Switch off rough.
    3. When the assembler is normaly pumped down, there should be back and gate switched on.
10. Check the alignment of chip wirebonds (with the Efitor) 
    1. We use the contacts b and d (a and c are for measurement team)
11. Create device on database and add the connection maps (if this is the first time we use the design), e.g. CS, S, G1-5, D, CD… and corresponding names on the bond map side. 
    1. This should become obsolete when the chip design team will start to automatically create wirebonding maps in the future, but it’s good practice to doublecheck the wirebonds.
12. Do a first chip health test to make sure there are no shorts
13. Check electrodes and gates from SEM/RABIES results to have an idea of potential issues
14. Choose CNT from charac report sheets

### Stapling

1. Approach SWAN to chip (chip should be horizontal when looking at it in the camera)
2. Bring microscope in by using its controller (it’s done manually at the moment)
3. After having decided what CNT to staple, focus the microscope on the correct cantilever (count by hand)
4. Start the coarse approach of the CAD to the chip until the alignment between device and cantilever spacing is good 
5. When you are close enough (check the shadow of the cantilevers against the device, and the alignment of the end of the cantilevers with the electrodes), choose the automatic approach to start going down. The automatic approach (using the attocubes) automatically decreases z by a fixed amount, while the current between CS and S and CD and D is measured, to see if touchdown has occured. When the current increases above a certain treshold, the approach automatically interrupts. 
    1. Touchdown might occur at the same time at both electrodes, or only at one side. 
6. Ground all connections on the matrix
7. Disconnect all connections on the matrix
8. Do chip health test, after switching off the microscope light,
    1. Depending on what you see (contacts at both electrodes, at one electrode, shortings, collapses…) you can do different operations:
        1. do I-V curve (this informs you on the quality of the contact you have between CNT and electrode, and possibly on the type of tube). Typical initial bias voltages are 1.5-2 V, not to push the CNT too much. You can decide to:
            1. Current anneal the tube further, by repeating the I-V curve while using a larger voltage range. Usually 8-9 V is when things get too harsh on the tube, and collpse events become more probable.
            2. Do gate dependance tests (i.e. scan the voltage applied to a gate while measuring the current through the CNT at a fixes S-D voltage.
            3. cut the tube already (whether the cutting happens mechanically or electrically depends on the specific electrode design/material. If the resistance of the electrodes is too high (of the order of 100 MOhm), you would need to apply a cutting voltage that would cause the CNT to collapse on the gates 
        
         ii. make another step down, and in case repeat the procedure done so far.
        

# Pick&Place stapling

### **Preparation**

1. Mount SQD sample holder on the transfer arm by screwing it on the appropriate mount (there are different mounts for different sampleholders/functions). 
2. Check all channels in Matrix are grounded from software 
3. Attach connectors (Nano-Ds) at the back of the sampleholder after removing the shorting caps from it. Each connector has 25 lines. There is only one way to insert the connectors, so it should not possible to invert them.
4. Mount fork on the SWAN (by screwing what are we screwing here???)
5. Mount CAD by screwing it on top of the SQD sampleholder
6. The chip should be horizontal
7. Check that the SWAN can move in all directions
8. Unlock the lid robot from the side of the cleanroom, bring the lid over the assembler and close the assembler by pressing the down arrow on the robot controller
9. Undo the three clamps on the lid, remove the rebot and lock it at the side of the cleanroom
10. Start pumping the assembler down. We have a rough pump (Back) prepumping the turbo pump (Turbo) and we have a rough pump (Rough) dedicated to create the low vacuum in the assembler. Pumps are always all on, we just close valves between Rough and assembler and between Turbo and assembler, depending on the operation. 
    1. From the jbox (controlling all valves on the system), switch rough on (back should  be on, with gate off)
    2. When pressure reaches 10^-1 hPa, switch the gate to on. Switch off rough.
    3. When the assembler is normaly pumped down, there should be back and gate switched on.
11. Check the alignment of chip wirebonds (with the Efitor) 
12. Create device on database and add the connection maps (if this is the first time we use the design), e.g. CS, S, G1-5, D, CD… and corresponding names on the bond map side. 
13. Do a first chip health test to make sure there are no shorts
14. Check electrodes and gates from SEM/RABIES/optical microscope (if existing) results to have an idea of potential issues
15. Choose CNT from charac report sheets

### Pick

1. Approach SWAN (i.e. fork) to CAD 
2. Bring microscope in by using its controller (it’s done manually at the moment) - to be made semiautomatic
3. After having decided what CNT to staple, focus the microscope on the correct cantilever (count by hand)
4. Check what is the distance between the end of the cantillevers and th eposition of the chosen CNT. In defining the starting posiiton of the fork, remember that you need to also correct for the angle on the CNT on the cantilever (i.e. if there is an angle, the fork needs to be further in than the central posiiton of the CNT).
5. Start the coarse approach of the fork to the CAD.
6. When you are close enough, choose the automatic approach to start going down. The automatic approach (using the attocubes) automatically decreases z by a fixed amount, while the current on the fork is measured, to see if contact has been made. When the current increases above a certain threshold, the approach automatically interrupts. 
    1. Contact might occur at the same time at both electrodes, or only at one side. 
7. Ground all connections on the matrix
8. Disconnect all connections on the matrix.
9. Check I-V curve on the CNT by passing some current rhough the CNT. This is usually a relatively conservative step, not to ruin the CNT. I-V curves can be done one after another at slightly increasingly voltages (usually still below 3-5 V) to see if current annealing improves the properties of the tube. If the CNT has interesting I-V dependance, you can retract the fork; the CNT should remain on the fork. If the CNT is not interested, “burn” it off the fork by passing a high current through it (10-15 V).
10. In either case, depending on what you want to see, retract the fork afterwards and check again I-V to verify whether the CNT is still there or not.

### Place

1. Approach the SWAN (i.e. fork + CNT) to chip (and specifically to the chosen device)
2. Bring microscope in by using its controller (it’s done manually at the moment) - to be made semiautomatic
3. Focus the microscope on the chip to make sure that everything is ok with it. Then, bring the fork in.
4. Check the alignment of the fork with the device.
5. Start the coarse approach of the fork to the chip until the alignment between device and cantilever spacing is good 
6. When you are close enough (check the shadow of the thines against the device, and the alignment of the end of the fork with the electrodes), choose the automatic approach to start going down. The automatic approach (using the attocubes) automatically decreases z by a fixed amount, while the current on the fork is measured, to see if contact has been made. When the current increases above a certain threshold, the approach automatically interrupts. 
    1. Contact might occur at the same time at both electrodes, or only at one side. 
7. Ground all connections on the matrix
8. Disconnect all connections on the matrix.
9. Check I-V curve on the CNT by passing some current rhough the CNT. 
10. Do gate dependance as well
11. Do chip health test, after switching off the microscope light,
    1. Depending on what you see (contacts at both electrodes, at one electrode, shortings, collapses…) you can do different operations:
        1. do I-V curve (this informs you on the quality of the contact you have between CNT and electrode, and possibly on the type of tube). Typical initial bias voltages are 1.5-2 V, not to push the CNT too much. You can decide to:
            1. Current anneal the tube further, by repeating the I-V curve while using a larger voltage range. Usually 8-9 V is when things get too harsh on the tube, and collpse events become more probable.
            2. Do gate dependance tests (i.e. scan the voltage applied to a gate while measuring the current through the CNT at a fixes S-D voltage.
            3. cut the tube already (whether the cutting happens mechanically or electrically depends on the specific electrode design/material. If the resistance of the electrodes is too high (of the order of 100 MOhm), you would need to apply a cutting voltage that would cause the CNT to collapse on the gates 
        
         ii. make another step down, and in case repeat the procedure done so far.