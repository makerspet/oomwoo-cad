OOMWOO One open-source vacuum robot spec

A brain-dump with some explanations. First of all, there are 3 living documents

- BOM.md https://github.com/makerspet/oomwoo/blob/main/BOM.md
- Companion article https://makerspet.com/blog/how-to-source-bom-for-oomwoo-open-source-vacuum-robot/
- 3D design spec https://github.com/makerspet/oomwoo-one-cad/blob/main/docs/SPEC.md

All 3D CAD design files live in this repo https://github.com/makerspet/oomwoo-one-cad

Let me go over each component and explain the thinking about it. Please let me know any comments/questions.

I will list the "recommended selection" as well as "backup alternatives".

- "Drive wheel assembly pair". Recommended - reuse Roborock S5 Max wheels because they are abundant in the aftermarket https://makerspet.com/blog/how-to-source-bom-for-oomwoo-open-source-vacuum-robot/#driving-wheels There is a backup alternative - Roborock S5 (non-Max) wheels. These are also abundant, but older. So, don't use those, lets stick with Roborock S5 Max.
- "Caster wheel". Recommended - caster wheel off iRobot Roomba I3/4/6/8, J7/Plus J7 E5/6 500 600 700 800 900 series. It appears to be the most abundant in the aftermarket. iRobot has used the same caster part using in all those models over years. Backup alternatives - plenty available off-the-shelf on AliExpress; or 3D print using TPU.
- "Suction fan". Recommended - BL24131616 10kPa. Recommended for 2nd vacuum version - 36 kPa from Roborock Saros 20, . Backup alternatives - fans with lower suction. Why 10kPa - modern vacuums use increasingly stronger suction. Old vacuums use mere 2-2.5kPa. Users want to see bigger kPa suction.
- "Main brush". Recommended - "Anti-tangle split single roller, rubber and bristles" for Roborock Saros. Users *strongly* want no tangling at all. This roller type seems one of the best - but *I may be wrong*. Another roller that appears to be great is "Anti-tangle hair-cutting dual roller, rubber and bristles", sold as replacement for Dreame vacuums. Please read about roller choices here https://makerspet.com/blog/how-to-source-bom-for-oomwoo-open-source-vacuum-robot/#main-brush Another option is 2 rollers, but having 2 rollers (I assume) will complicate your CAD design. So single (or single split?) roller seems best for 1st vacuum version. The 1st vacuum version's name is OOMWOO One.
- "Battery pack + BMS". Required - the standard Roborock battery. Roborock has been using it over many years and many models. It comes with built-in protection and thermistor. No obvious alternatives.
- "2D LiDAR". Recommended - "PCB mark X-WPFTB-V2.6.2, possibly Camsense". However, there are many alternatives. Some users own different LiDARs - and want to reuse them. So, we should let users pick their LiDAR - by 3D printing a custom mounting bracket.
- "Compute Module". Required - Raspberry Pi CM4 or CM5. CM4 and CM5 have identical dimensions.
- "I/O board". Required - custom-designed PCB https://github.com/makerspet/oomwoo-io-board. The I/O board will have all motor/sensor connectors, driver ICs. The "Compute Module" will plug into the I/O board. The I/O board shape/dimensions is *not* set - it will be decided based on your CAD design.
- "Cliff sensors". Required - "cliff sensor + bumper switches bundle" iRobot Roomba 500 600 700 800 528 552 564 595 560 570 610 615 620 625 630 650 off-the-shelf, abundant in the aftermarket. The "bundle" includes 4 IR cliff sensors and 2 bumper switch assemblies. Backup alternatives - if this bundle doesn't work for you, let me know, I will suggest alternatives. Please note - some vacuums have 4 IR cliff sensors, while others have 6. The typical 4-sensor placement is (1) around the caster wheel (in the front) and in front of each driving wheel. 6-sensor vacuums add one sensor just behind each driving wheel. I've noticed some vacuums have 5 sensors (only one driving wheel has 2 cliff sensors). Generally, I'd like to have 6 cliff sensors, but 6-sensor bundles are harder to find/purchase.
- "Bumper switches". Required - please use the iRobot bundle. If you find a problem using these - let me know.
- "Main brush motor, gearbox". Required - let's use one off Roborock S5 because it is abundant. However, this assembly fits Roborock brushes with bristles (which tangle hair badly). So, you may need to design some sort of adapter to accommodate tangle-free brushes. Backup alternatives - we can buy the DC motor and 3D print gears using an SLA resin printer. But I'd like to avoid this additional complexity if possible. FYI, commercial vacuums use RS390 and RS395 DC motors.
- "Side brush". Recommended - "2-arm curved" side brush from Roborock Saros. It seems better at anti-tangling (but I haven't checked). Backup alternatives - older Roborock side brushes or Dreame side brushes.
- "Side brush motor". Recommended - only one side brush, extendable, from Roborock Qrevo https://www.alibaba.com/product-detail/Roborock-Telescopic-Robotic-Arm-Side-Brush_1601598853246.html Backup alternatives - if the recommended one doesn't work for you, let me know, I will check Dreame X40 and Dreame X50 extendable side brush assemblies.
- "Wall sensor". Required - two little custom-designed PCB (one left, one right). These sensors (1) detect IR signal from the dock (2) detect wall (in a crude way). Backup alternative - a Roborock wall sensor assembly is available on AliExpress, but not abundant.
- "Dock homing sensor". Required - a little custom-designed PCB with two IR sensors, in vacuum rear front. Backup alternatives - let me know if there is a problem and I will check.
- "Carpet sensor". Required - ultrasonic 300kHz material sensor, fixed 30mm distance above floor. This model for your initial CAD design https://www.aliexpress.us/item/3256808845934210.html and this model for volume https://htwsensor.en.made-in-china.com/product/jARpDPKoaxVz/China-300kHz-Carpet-Material-Recognition-Sensor-for-Robotic-Vacuum-Cleaner-Ultraosinc-Sensor-Transducer.html .
- "Charging contacts" (on the robot). Recommended - DIY using a nickel-plated steel strip (purchased on AliExpress). Located in the robot's rear around the homing IR sensor PCB. No springs. Strip width/length - up to you. AliExpress has 10-12mm. Each contact (positive, ground) connects to a PCB connector cable. The contact-to-wire connection could be accomplished by designing a tiny 3D printed "terminal'. Have a machine screw pressing the (stripped) wire against the strip.
- "Mop motor assembly". Recommended - 2 rotary/disk mops. One static, one extendable. Use Roborock Qrevo FlexiArm https://www.alibaba.com/product-detail/Mop-Deceleration-Motor-Retractable-Mopping-Module_1601599652498.html Backup alternatives - if the Roborock Qrevo doesn't work for you, I can search Chinese ODM making Dreame MopExtend.
- "Obstacle avoidance camera". Recommended - 1x front-facing OV5647 with a 16-pin flexible cable, ~130 degree FOV. Backup alternatives - none that are cheap.
- Bagless vs bag dock. Recommendation: bagless. Why? Multiple users requested bagless; no-one asked for bags. Also, no consumable bag purchase/cost. The dock's dust bin can be 3D printed. However, bagged is easier to engineer. Bagless needs reliable separation (a working cyclone + washable filter). Designing a good cyclone is important. A poor one sends fine dust straight to the filter, clogs the filter, and suction dies.
Auto-empty design. Recommendation: bottom extraction (Roborock style). Why? This is what my Claude says:
- side brush with extensible arm assembly - expensive, hard to find retail. Roborock uses lots of gears; the brush DC motor both actuates the brush and the arm. Design from scratch using a little timing belt, aluminum timing pulleys and a geared DC motor (metal gearbox comes with the motor). 3D-print the assembly enclosure This avoids having to 3D print gears and keeps the build inexpensive.

=== Claude =====================================

1. Gravity is on your side. Dust settles to the bottom of the bin, and bottom extraction pulls it downward into the dock bin. A dedicated side/rear vent higher on the bin fights gravity — you're asking the fan to lift settled dust before it can carry it out.
2. Simplest robot-side port: one flap. You add a single spring/gravity trap door on the bin bottom — no second sealed opening in the bin. A dedicated vent means a second aperture you must seal against leaks during every vacuuming run.
3. Flat, forgiving dock mating. The dock side is just a gasketed hole in the base plate; the robot parks over it. Flat-plate-to-flat-plate tolerates alignment error far better than threading a nozzle into a port (which a dedicated vent requires). Your ramp/alcove already gets the robot "close enough," and a broad base port forgives the rest — same philosophy as oversizing the charging pads.
4. Proven and measurable. It's the dominant industry design, so you can study/measure a real Roborock dock to de-risk the printed geometry.
5. It decouples from your crowded rear. Your rear is already busy — vertical contacts + mop wash tray (back-in docking). Putting auto-empty on the underside keeps it spatially separate from that cluster.

The hard part is the same for both: the valve + the airflow path

Whichever port you choose, the real engineering is the flap valve and the makeup-air path, not the port location:

- The flap must do two contradictory things: seal tightly during vacuuming (so the robot's own fan doesn't lose suction through the auto-empty port) yet open freely under the dock's airflow. Bottom extraction makes this natural — the dock's downward suction pulls an inward/downward flap open, and spring + gravity reseat it. A high side/rear port needs a more deliberate valve.
- You must give the emptying airflow a makeup-air inlet, or the dock fan just pulls a vacuum against a sealed bin and moves nothing. The clean trick (and what Roborock does): let the dock's suction draw makeup air in through the robot's own intake mouth — which is right there at the bottom — so air sweeps through the bin and out the bottom port, entraining settled dust on the way. Design the bin so that emptying airflow traverses the whole bin volume rather than short-circuiting between two nearby openings. This is the single thing that determines whether auto-empty actually evacuates dust vs. just whistling.

Why not the dedicated bin vent

- Its only real advantage is a seal that's higher and away from floor-level dust. That's outweighed by: a second aperture to seal, a nozzle-to-port mating that's alignment-fussy, fighting gravity, and more total seals — all worse for a printed part where every seam is a potential leak. Not worth it.

Two build-specific notes

- Bagless synergy: bottom extraction drops dust straight down into the dock's printed bin sitting in the base — exactly what you want for the bagless, printed-container design you chose. Gravity does half the work of separating debris before the dock cyclone/filter even acts.
- Since the robot backs in rear-first (mop-dock orientation), position the dock base's suction hole under wherever the robot's bottom bin-port ends up in the docked position — likely forward of the mop/contact cluster. This is part of the same frozen dock interface as the contacts and the beacon, across all three tiers.

So: pull from underneath through a single bottom trap-door, let makeup air come in via the robot's intake so the flow sweeps the bin, and drop it into the printed dock bin by gravity. The dedicated-vent approach adds sealing complexity for a benefit you don't need.


Following modern (2026) consumer mop robot design, OOMWOO One requires

- one right front side brush (not two), with an extendable arm (swings out to the side to clean under cabinets)
- mop is 2-disk rotary (not roller for now); the right mop is extendable (swings out to the side to clean under cabinets); the left mop is fixed
- mop disks land into the dock tray (for mop washing, drying)
- having charging contacts on the *rear vertical face*
  - charging contacts cannot be on the robot's underside because this is where the mop wash tray sits
- vacuum *backing* into the (wash) dock (not driving in front-first)
- robot's dock homing sensor must be on the *rear vertical face* between the charging contacts
- robot's charging contacts are "dumb" (not spring-loaded), use an nickel-plated steel strip
  - nickel-plated steel strips resist corrosion, scratching
- charging contacts on the dock have to be spring loaded, with gold-plated pogo pins, 4A 20.1V to provide 65W
- TODO bagless or not
- LiDAR must be inset 10+cm from vacuum's enclosure edges
  - because LiDAR sensor has a ~10cm dead zone around it
- place LiDAR slightly off-vacuum-center
  - this allows capturing scans from new viewpoints while vacuum spins in-place without getting stuck (usually when lost to regain its whereabouts on the map)
- need to lift mops (when traveling over carpet) 12mm
- need a [carpet sensor](https://makerspet.com/blog/how-to-source-bom-for-oomwoo-open-source-vacuum-robot/#carpet-sensor) (ultrasonic ~300kHz) placed in front of main brush; carpet detect causes mops to lift, stop spinning, main brush to spin appropriately for carpet
  - carpet sensor detects carpet ahead of time as the vacuum travels forward, so the mop is always lifted over carpet
- need 2 side wall sensors (left, right)
  - wall sensors detect dock presence (by receiving IR signal from the dock) and act as a crude wall following (intensity based) sensor
  - wall sensor has to be a small custom PCB
- drving wheels should be centered, wide apart
  - let's try reusing [Roborock S5 Max assembly](https://makerspet.com/blog/how-to-source-bom-for-oomwoo-open-source-vacuum-robot/#driving-wheels) because it is abundant in the aftermarket
  - each wheel comes with a wheel drop sensor (a microswitch)
  - FYI some vacuums don't center driving wheels exactly
- robot-to-floor gap is largely defined by the drive wheels
- caster wheel - front center
  - let's try reusing the abundant [iRobot Roomba](https://makerspet.com/blog/how-to-source-bom-for-oomwoo-open-source-vacuum-robot/#caster-wheel)
- I/O board and compute module - front center top, shape TBD
  - board has pushbuttons
- battery pack - reuse abundant standard [Roborock battery pack](https://makerspet.com/blog/how-to-source-bom-for-oomwoo-open-source-vacuum-robot/#battery-pack)
  - place battery pack on the vacuum bottom, with an access door with screws, roughly under the I/O board or slightly behind, roughly centered to equalize pressure on both wheels and mops
  - TODO check if battery should be close to mops for cleaning pressure


## Dock

### Specs

- ~use an external certified 24 V DC brick (200–350 W)~
  - the dock only sees 24V?
  - inherit the brick's UL/CE certification?
  - ~reuse 25.2 V stick-vac motors, e.g. Dreame M10-E-4 (25.2 V, 310 W) handheld motor, use for auto-empty~
- power 1600W, see [X20 dock teardown](dock_teardown_x20.pdf)
- ~dock contains USB PD sink, converts power to 20-24V charger contacts~
  - dock charger contacts check for robot's presence (resistance), enable power only when robot is present
- skip hot air dry, use a regular fan
  - Hot air dries the mop in ~2–3 h instead of ~6. But the robot sits docked for hours anyway.
  - Dropping the heater removes your biggest power draw and biggest thermal-safety risk.
- bagless
  - No consumable lock-in. The bin is a printed part.
  - Downside: emptying a dusty bin by hand. The dock bin is far larger than the robot's, so you empty it ~monthly instead of every run. Design a wide opening + lid to limit the dust puff.
  - Bagged is significantly easier to engineer — the bag is the container and the filter, so there's no cyclone to design.
  - Bagless needs real separation (a working cyclone + washable filter), and the cyclone is the main engineering risk of this choice — a poor one sends fines straight to the filter, it clogs, and suction dies.
  - Maybe prototype the auto-empty tier bagged to de-risk the port/sealing/motor work, then move to bagless once you've validated a cyclone geometry. Ship bagless.
- bottom extraction auto-empty
  - why? proven, Roborock style; gravity helps dust fall/evacuate vs non-bagless rise; only one, simple robot-side port, one flap - no sealed opening in the robot's dust bin needed; robot-to-dock flat plate-to-plate gasketed mating is relatively simple vs bagged nozzle-into-the-port mating; frees us space in the robot's rear
- tubing, see [X20 dock teardown](dock_teardown_x20.pdf)
  - water 9mm OD clean, 11mm OD dirty, clean mop spray 6mm OD
  - air auto-empty ID 29mm OD 33mm
- canister present sensors: 2x (clear + dirty water canisters): magnet embedded into canister, hidden hall, see [X20 dock teardown](dock_teardown_x20.pdf)
- water level sensors
  - clear water tank : floaters magnet/hall
- TBD sensors
  - TBD dock-side IR turbidity sensor
  - TBD thermistor + independent thermal fuse
  - TBD dock base leak/flood sensor
- TODO cleaning solution
- TBD hot water mop wash
- TBD hot air mop dry
- safety
  - Mains stays outside (certified brick)?
  - Physically separate wet section from electronics; drip loops, drainage, a dam/lip toward the contacts.
  - Presence-detect the robot, energize charge contacts only when the robot is docked
  - If using heater: redundant thermal cutoff (thermistor + independent thermal fuse), never fan-less.
  - Document as advanced build.
