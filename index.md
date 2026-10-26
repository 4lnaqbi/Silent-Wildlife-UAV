---
title: Silent Wildlife UAV | MEC 482
---

# Silent Wildlife UAV
### AI-Powered Low-Noise Drone for Endangered Wildlife Monitoring

**Abu Dhabi University — College of Engineering**  
**MEC 482: Introduction to Mechatronics**

---

## Home

### Team members

| Name | University email |
|---|---|
| Mansour Khalid Alnaqbi | 1086214@students.adu.ac.ae |
| Shamma Nasser | 1088805@students.adu.ac.ae |
| Alyazia Mohamed Alshehhi | 1090139@students.adu.ac.ae |
| Salim Mohamed Alkathiri | 1081901@students.adu.ac.ae |

**Project supervisor and course professor:** Dr. Claudio Vignola  
**Institution:** Abu Dhabi University, United Arab Emirates

## Project overview

Our project proposes a low-noise unmanned aerial vehicle (UAV) for detecting and monitoring endangered wildlife while minimizing disturbance to animals and their natural habitats. We aim to find the best practical balance among **low acoustic noise, adequate thrust, reliable onboard AI detection, and efficient energy use**.

We plan to reuse parts from our previous hybrid VTOL search-and-rescue drone, including the chassis and suitable propulsion and flight-control hardware. Proposed upgrades include toroidal propellers, an onboard camera and AI computer, and data logging during GPS waypoint missions.

**Project stage:** Concept development and component selection.  
**Target flight endurance:** Approximately **30 minutes**, subject to verification.  
**Scope note:** The course's biometric/bio-inspired engineering requirement and safety constraints must be approved by the instructor before full development.

## Research question

**Can a UAV equipped with optimized toroidal propellers and onboard animal-detection AI reduce acoustic disturbance while achieving useful thrust, power efficiency, and survey endurance?**

Our hypothesis is that a suitable toroidal design may reduce propeller-generated noise compared with an appropriate baseline while maintaining enough thrust for the intended mission. We will test this hypothesis rather than assuming an improvement.

## Biomechanics background and initial specifications

### Biological inspiration and engineering principle

This project is motivated by wildlife-sensitive monitoring. Toroidal propeller tips form closed loops, changing the airflow and tip-vortex behavior compared with conventional exposed-tip propellers. **A toroidal propeller is not automatically biomimetic:** the team will research and obtain approval for a specific biological feature that can be defensibly transferred into the proposed design.

### Preliminary component options

| Subsystem | Preliminary selection | Alternative / comment |
|---|---|---|
| Drone | Reuse the existing hybrid VTOL platform | Final airframe may be modified |
| Propeller | Two-blade toroidal | Three-blade toroidal for comparison |
| Camera | Raspberry Pi Camera Module 3 | Select after field-of-view and altitude analysis |
| Onboard AI | Raspberry Pi 5 with AI HAT+ | Arduino UNO Q (compatibility/YOLO speed to verify) |
| Animal detection | YOLO object detection | Species recognition requires suitable training data |
| Tracking | Multi-object tracking | Kalman-filter-based tracking is one option |
| Navigation | Existing compatible flight controller + Mission Planner | Autonomous waypoint plan subject to approvals |
| Battery | 4S 6750 mAh LiPo initial candidate | 4S 10000 mAh for energy comparison |
| Endurance | 30-minute target | Not yet demonstrated |

## System kinematics

The four-motor vehicle creates thrust by accelerating air through rotating propellers. The team will compare two- and three-blade toroidal configurations using controlled measurements of RPM, static thrust, torque or electrical power, and vibration.

For propeller speed \(N\) in revolutions per minute:

\[\omega = \frac{2\pi N}{60}\]

where \(\omega\) is angular speed in rad/s.

## System dynamics

### Thrust-to-weight ratio

\[\mathrm{TWR} = \frac{T_{\mathrm{total}}}{mg}\]

The previous rescue prototype had a documented mass of approximately **1.409 kg**. Its calculated weight was about **13.82 N**, or approximately **3.46 N per motor** for four-motor hover. These values are **previous-platform figures** and must be recalculated for the redesigned aircraft.

### Electrical power

\[P = VI\]

where \(P\) is power in W, \(V\) is voltage in V, and \(I\) is current in A.

### Endurance estimate

\[t_{\mathrm{h}}\approx\frac{E_{\mathrm{usable}}\,(\mathrm{Wh})}{P_{\mathrm{average}}\,(\mathrm{W})}\]

An endurance calculation must include the complete mass and average power requirements of motors, camera, computer, cooling, and other electronics. Flight testing is required to validate predictions.

## Design optimization

### Preliminary weighted decision matrix

Scores are **engineering assumptions**, not experimental test results. Ratings use a scale of 1 (poor) to 5 (excellent).

| Criterion | Weight | Two-blade toroidal | Three-blade toroidal |
|---|---:|---:|---:|
| Noise reduction | 30% | 4 | 3 |
| Static thrust | 25% | 3 | 5 |
| Power efficiency | 20% | 4 | 3 |
| Weight | 10% | 5 | 3 |
| Manufacturing cost | 10% | 5 | 3 |
| Structural robustness | 5% | 3 | 4 |
| **Weighted score** | **100%** | **78 / 100** | **71 / 100** |

**Initial selection:** The two-blade toroidal design is our first prototype candidate. The final choice will be based on repeated, matched-thrust measurements of noise and electrical power, as well as adequate static thrust.

Toroidal propellers are **not silent**; geometry, RPM, airflow and vibration still generate sound.

## Design and manufacturing

We plan to reuse usable components from the previous drone and develop original CAD for the modified airframe and integration parts. Potential student-designed fabricated parts include a camera mount, onboard-computer bracket, and custom propeller prototypes.

**Safety:** Printed experimental propellers must be inspected, balanced, and tested in an instructor-approved guarded test stand. Their suitability for actual flight cannot be assumed.

## AI processing and wildlife detection

The proposed onboard processing chain is:

**Camera → Onboard computer → YOLO detection → Object tracking → Timestamp / positioning → Data storage**

YOLO detects animals in video frames by drawing bounding boxes and estimating detection confidence. Species-level identification requires suitable trained examples; YOLO by itself does not guarantee identification of endangered species. A tracking algorithm can associate detections across successive frames.

Drone GPS provides the **aircraft** location. Estimating an animal's location also requires information such as camera pointing direction, altitude and calibration.

**Processor options:** Raspberry Pi 5 + AI HAT+ is the provisional choice for onboard YOLO. Arduino UNO Q is a lower-cost alternative to evaluate, but actual model compatibility, inference speed, camera interface and power draw must be verified before selection.

## Autonomous navigation using Mission Planner

The planned mission is:

1. Define a conservation survey area and prepare GPS waypoints in Mission Planner.
2. Upload the approved flight plan to a compatible flight controller.
3. Carry out preflight and safety checks.
4. Follow the waypoint mission, collecting camera images.
5. Run animal detection onboard and record detections.
6. Return to the launch location and review the data.

The flight controller handles navigation and stabilization; YOLO handles visual detection. Autonomous or outdoor flight remains subject to instructor approval and applicable UAV/wildlife permissions.

## Battery selection and 30-minute flight target

| Battery | Nominal energy | Usable energy at assumed 80% | Example endurance at constant 220 W |
|---|---:|---:|---:|
| 4S 6750 mAh LiPo | 99.9 Wh | 79.9 Wh | ~21.8 minutes |
| 4S 10000 mAh LiPo | 148 Wh | 118.4 Wh | ~32.3 minutes |

These are **illustrative energy-only calculations**, not flight-test results. The larger battery is heavier and may increase propulsion power, so its true endurance advantage cannot be confirmed without testing. Start by measuring total aircraft mass and power rather than purchasing a battery based on capacity alone.

## Preliminary cost breakdown

| Item | Estimated AED |
|---|---:|
| Raspberry Pi 5 | 459 |
| AI HAT+ | 446 |
| Raspberry Pi Camera Module 3 | 172 |
| Storage, cooling, mounting and power regulation | 275 |
| Battery allowance | 550 |
| Propeller development and bench testing | 737 |
| **Estimated additional project cost** | **2,639** |

These are preliminary budgeting allowances, **not final supplier quotations**. The proposed scope exceeds the MEC 482 default AED 800 budget and requires instructor approval, a smaller scope, or access to existing university equipment.

## Data collection and experimental validation

The team will compare propeller configurations in a safe, repeatable test setup. At least **10 restarted trials per configuration** will be used where required by the project brief.

| Measurement | Unit |
|---|---|
| Static thrust | N |
| Noise at fixed microphone location | dBA |
| Rotational speed | RPM |
| Electrical voltage | V |
| Electrical current | A |
| Electrical power | W |
| Propeller mass | g |
| Vibration | m/s² or another documented measure |

We will report averages, standard deviations, trial conditions and limitations, including **noise measured at matched thrust**. All actual trial measurements will be uploaded after testing, without fabricated results.

## Safety and approval

- Protect operators during all propeller tests with an appropriate guard and remote shutdown.
- Check battery wiring, current limits, charging procedures, and mechanical integrity.
- Obtain course approval for the existing **4S battery**, since it exceeds the brief's usual 12 V or less electrical boundary.
- Do not conduct uncontrolled flight under the project brief.
- Seek any required UAV and wildlife-monitoring approvals before conducting field tests.

## Project progress

### Previous platform: completed work

The earlier offshore rescue prototype included original CAD and structural evaluation, integration of a propulsion and detection system, and an outdoor test demonstrating takeoff, hover, payload carriage/release and landing. These results belong to the **previous VTOL project** and do not demonstrate the wildlife system's current capabilities.

### Current wildlife project: concept stage

- Defined the endangered-wildlife monitoring mission.
- Identified two- and three-blade toroidal propellers for comparison.
- Drafted a weighted propeller decision matrix.
- Investigated camera and onboard AI options.
- Established a provisional 30-minute endurance target.
- Identified Mission Planner as the proposed route-planning software.

### Next steps

- Confirm project scope, budget, safety and the biological mechanism with Dr. Claudio.
- Inventory and inspect reused drone hardware.
- Develop original CAD and fabricate initial test articles.
- Measure guarded bench thrust, noise and power.
- Select the computing, camera and power solution based on compatibility tests.
- Implement the detection and logging prototype.
- Conduct approved repeatable validation and report measured results.

## Presentations

- **Presentation 1:** Concept, research question, earlier VTOL platform, proposed components and design decisions.
- **Presentation 2:** CAD, mechanism development, electronics/control architecture and early tests.
- **Final presentation:** Safe prototype demonstration, data analysis, design optimization and conclusions.

Presentation slides, photographs, test videos, source code and CAD will be linked as they become available.

## Bibliography and resources

1. [MIT Lincoln Laboratory — Toroidal Propeller](https://www.ll.mit.edu/partner-us/available-technologies/toroidal-propeller-0)
2. [Ultralytics — YOLO Documentation](https://docs.ultralytics.com/)
3. [Raspberry Pi — Documentation](https://www.raspberrypi.com/documentation/)
4. [Arduino — Official Website](https://www.arduino.cc/)
5. [ArduPilot — Mission Planner](https://ardupilot.org/planner/)
6. Alnaqbi, M. K., Nasser, S., Alshehhi, A. M., Dol, S. S., & Alavi, M. *Structural Evaluation and System Integration of a Hybrid VTOL Drone for Offshore Search and Rescue* (previous project manuscript).

---

*Silent Wildlife UAV — MEC 482, Abu Dhabi University. Project supervisor and course professor: Dr. Claudio Vignola.*
