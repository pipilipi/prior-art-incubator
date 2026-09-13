# Defensive Technical Disclosure  
## Adaptive Light/Dark Recovery Control for Concentrated Perovskite Photovoltaics on a Rotating Thermal Carrier

**Document version:** 0.1  
**Draft date:** 2026-09-13  
**Public disclosure date:** _Not yet established — fill in only when this document is actually made publicly accessible._  
**Author / inventor:** _To be completed before public publication._  
**Status:** **SPORAN / TRAŽI EKSPERIMENT** — physically plausible and supported by adjacent literature, but the central lifetime-energy advantage is not yet experimentally demonstrated.  
**Purpose:** Defensive technical publication / prior-art disclosure. This document is not a patent application and does not assert that the broad rotating-PV architecture is novel.

> **Publication warning.** A private draft is not a public disclosure merely because it has been written. For a defensive publication, the final document should be made publicly accessible in a durable, date-verifiable location. Public disclosure can also affect the author’s own future patent rights, particularly outside jurisdictions with inventor grace periods.

---

## 1. Abstract

This disclosure describes a photovoltaic operating architecture in which a metal-halide perovskite photovoltaic surface is moved repeatedly between a concentrated-illumination zone and a dark recovery/cooling zone. A preferred mechanical embodiment is a thermally conductive rotating drum or cylinder carrying a perovskite photovoltaic layer or segmented perovskite photovoltaic cells around part or all of its circumference.

The broad concepts of rotating photovoltaic cells, concentrated illumination, sequential movement out of a focal zone for cooling, variable rotational speed, start-stop motion, internal coolant channels, heat pipes, and slip-ring electrical extraction are already present in earlier patent literature and are **not claimed here as new**.

The specific subject intentionally disclosed here is the combination of those known mechanical techniques with **perovskite-specific recovery-state control**. The controller does not select speed or position solely from instantaneous irradiance or temperature. Instead, it may maintain a state history for each photovoltaic segment, including cumulative photon dose, time under concentrated illumination, time in darkness, temperature history, cycle count, recent normalized power, estimated state of health, and an empirically calibrated recovery function. The controller then selects angular velocity, dwell time, segment ordering, concentration, electrical operating state, and/or cooling intensity to maximize cumulative lifetime electrical energy rather than instantaneous power alone.

Natural low-irradiance events, including passing clouds, shading, eclipse, night, pointing interruptions, or spacecraft attitude changes, can be intentionally incorporated as extended recovery periods rather than treated only as lost production time.

The central engineering hypothesis is not that a perovskite segment must return to a hypothetical “100% regenerated” state after every dark interval. Instead, the system seeks the **marginal optimum**: the dark interval is extended only while the additional recovery or reduction in degradation is worth more than the additional photovoltaic inventory, mechanism mass, or opportunity cost required to provide that interval.

The primary validation metric is therefore:

\[
E_{\mathrm{life}}=\int_0^{T_\mathrm{end}} P(t)\,dt
\]

and, depending on application:

\[
\frac{E_{\mathrm{life}}}{A_{\mathrm{PV}}},\qquad
\frac{E_{\mathrm{life}}}{m_{\mathrm{system}}},\qquad
\frac{E_{\mathrm{life}}}{A_{\mathrm{aperture}}}
\]

rather than peak efficiency or T80 alone.

---

## 2. Technical problem

Metal-halide perovskite solar cells can exhibit high photovoltaic efficiency and can operate under concentrated illumination. Their practical deployment, however, is constrained by interacting degradation mechanisms that may include:

- temperature-dependent performance loss;
- light- and bias-induced ion migration;
- creation and annihilation of electronic traps;
- reversible or partially reversible photochemical or structural changes;
- composition-dependent phase segregation;
- thermal and illumination-driven lattice strain;
- interface degradation;
- irreversible chemical degradation;
- mechanical and thermal fatigue.

These processes do not necessarily have the same time constant and do not necessarily respond in the same way to darkness.

Accordingly, the engineering problem is **not** simply “cool the cell after it gets hot.” The broader problem is to determine whether a controlled sequence of illumination and darkness can increase the total usable energy extracted from a given perovskite photovoltaic inventory over its operating life, especially when the illuminated segment is subjected to moderate optical concentration.

---

## 3. Core disclosed concept

A photovoltaic apparatus comprises:

1. a metal-halide perovskite photovoltaic active surface divided physically or logically into a plurality of addressable or trackable segments;
2. a movable carrier, preferably a rotating drum, cylinder, belt, loop, reel system, carousel, disk, polygonal rotor, or equivalent moving support;
3. an optical system that directs solar or artificial radiation at an irradiance greater than the ambient incident irradiance onto at least one active segment;
4. a region in which a previously illuminated segment receives substantially less irradiance, preferably darkness or near-darkness;
5. a thermal path from the photovoltaic active layer to a thermal carrier, coolant, heat pipe, radiator, heat exchanger, thermal reservoir, phase-change medium, or other heat rejection system;
6. a motor or actuator capable of controlling motion, preferably a stepper motor, servo motor, direct-drive motor, or indexed actuator;
7. one or more sensors for irradiance, photovoltaic power, current, voltage, temperature, angular position, coolant condition, or related state variables;
8. a controller that maintains an estimated **recovery state and degradation history** for one or more photovoltaic segments; and
9. a control law that changes exposure time, dark time, angular speed, dwell position, segment sequence, concentration, cooling, or electrical loading according to that history.

The system can produce continuous electrical output even though each individual segment operates intermittently, because different segments sequentially occupy the illuminated region.

---

## 4. Preferred mechanical embodiment: rotating thermal drum

### 4.1 Structure

The preferred embodiment uses a hollow thermally conductive drum, for example aluminum or another lightweight thermally conductive material. A perovskite photovoltaic stack is formed directly on, integrated with, bonded to, laminated onto, or mechanically retained by the curved outer surface.

Where electrical isolation from a metallic drum is required, the PV stack can be separated from the drum by a thin electrically insulating but thermally conductive layer. The particular photovoltaic layer sequence is not essential to the control concept.

The drum can include one or more of:

- internal liquid-coolant passages;
- a stationary internal cooling manifold;
- heat pipes connected through the shaft;
- a pumped two-phase loop;
- an external coolant jacket outside the illumination region;
- conductive end plates;
- a spacecraft radiator connection;
- a terrestrial air or liquid heat exchanger;
- emissive surfaces intentionally located in non-illuminated regions;
- thermal storage material to suppress short temperature excursions.

The thermal carrier is preferably designed to minimize **temperature amplitude** during light/dark cycling. Darkness is used for optoelectronic/ionic recovery and for heat rejection, but the device should not unnecessarily drive the perovskite through large temperature swings if those swings cause lattice-strain fatigue.

### 4.2 Optical exposure

A reflector, lens, Fresnel element, trough, dish, waveguide, non-imaging concentrator, or equivalent optic directs concentrated light onto a selected angular sector.

A practical development range is moderate concentration, for example:

\[
1.5 \le C \le 10
\]

with **2–4 suns** as a preferred initial experimental region, not as a claimed universal optimum.

The optical footprint can be:

- a narrow line;
- a finite angular sector;
- several separated sectors;
- a shaped intensity profile;
- an adjustable-width zone;
- a scanned zone;
- a zone whose concentration factor changes under controller command.

The system is not limited to a fixed focal width.

---

## 5. Duty cycle is a controlled variable, not a fixed geometry

Let:

- \(\theta_L\) = angular width of the illuminated sector;
- \(\theta_D\) = angular width of the dark sector;
- \(\omega_L\) = angular velocity while a given segment traverses the illuminated sector;
- \(\omega_D\) = angular velocity while it traverses the dark sector.

Then:

\[
t_L=\frac{\theta_L}{\omega_L}
\]

\[
t_D=\frac{\theta_D}{\omega_D}
\]

and:

\[
D=\frac{t_L}{t_L+t_D}
\]

where \(D\) is the illumination duty cycle for an individual segment.

This is important because a fixed drum geometry does **not** require a fixed light/dark duty cycle. An indexed or stepper-driven drum may travel rapidly through the illuminated sector and slowly through the dark sector, or the reverse. It may also stop at selected angular positions.

Thus the controller may change \(t_L\) and \(t_D\) without changing drum diameter or optical geometry.

A larger drum may still be useful because it provides:

- greater active area;
- greater thermal mass;
- more space for segmentation and electrical routing;
- larger internal cooling geometry;
- reduced curvature for a given PV layer;
- more physical dark surface available for heat rejection.

However, increased diameter is not itself equivalent to increased recovery time when rotational speed is freely controlled.

---

## 6. Perovskite-specific segment state

Each physical or logical segment \(i\) may be represented by a state vector:

\[
S_i=
\left[
Q_i,\;
t_{L,i},\;
t_{D,i},\;
T_i,\;
T_{i,\mathrm{hist}},\;
N_i,\;
P_{i,\mathrm{norm}},\;
V_{OC,i},\;
I_{SC,i},\;
FF_i,\;
H_i,\;
R_i
\right]
\]

where, depending on implementation:

- \(Q_i\): accumulated radiant dose or absorbed photon dose;
- \(t_{L,i}\): recent and/or cumulative illuminated time;
- \(t_{D,i}\): time since the segment last left the illuminated zone;
- \(T_i\): estimated current temperature;
- \(T_{i,\mathrm{hist}}\): temperature history or thermal-cycle amplitude;
- \(N_i\): number of illumination/recovery cycles;
- \(P_{i,\mathrm{norm}}\): power normalized for current irradiance and temperature;
- \(V_{OC,i}\): open-circuit-voltage-related health indicator where measured;
- \(I_{SC,i}\): current-related health indicator where measured;
- \(FF_i\): fill-factor-related health indicator where measured;
- \(H_i\): estimated long-term state of health;
- \(R_i\): estimated short-term recoverable state.

Not every embodiment needs every variable.

The key disclosed idea is that the controller can use **history-dependent state**, rather than only current irradiance and temperature.

---

## 7. Recovery function and marginal recovery criterion

This disclosure does not assume that perovskite recovery follows one universal exponential law.

An empirical recovery model may be obtained experimentally:

\[
R_i = F(t_D,\,T,\,Q_i,\,H_i,\,C,\,V_\mathrm{bias},\,\text{composition},\,\text{device architecture})
\]

For some materials, the function may be approximated by one or more exponential terms:

\[
R(t)=R_\infty-\sum_k a_k e^{-t/\tau_k}
\]

but this form is only a fitting option, not a required physical assumption.

The controller can estimate the marginal benefit:

\[
M(t_D)=\frac{\partial E_{\mathrm{future}}}{\partial t_D}
\]

and terminate the dark interval when the expected additional lifetime-energy benefit falls below the cost associated with extending the interval.

In practical terms:

> The objective is **not complete recovery**. The objective is to stop waiting when further recovery becomes too small to justify additional PV inventory, mechanism size, or lost utilization of that specific segment.

This explicitly includes the possibility that 10–20% of the maximum possible dark interval may produce most of the economically useful recovery.

---

## 8. Control objective

A controller may seek to maximize:

\[
J =
E_{\mathrm{life}}
-\lambda_m m_{\mathrm{system}}
-\lambda_a A_{\mathrm{aperture}}
-\lambda_M E_{\mathrm{motor}}
-\lambda_T \Phi_T
-\lambda_S \Phi_{\mathrm{stress}}
\]

where the penalty terms can represent system mass, collector aperture, motor energy, temperature excursions, and mechanical/thermal cycling stress.

Simpler real-time objectives are also disclosed, including maximizing:

\[
\frac{E_{\mathrm{life}}}{m_{\mathrm{system}}}
\]

for spacecraft;

\[
\frac{E_{\mathrm{life}}}{\mathrm{cost}}
\]

for terrestrial systems; or:

\[
\frac{E_{\mathrm{life}}}{A_{\mathrm{PV}}}
\]

when perovskite inventory is the limiting resource.

For a simple first-order comparison, with concentration \(C\), optical efficiency \(\eta_{opt}\), and segment illumination duty \(D\), the instantaneous power productivity per total PV area relative to a 1-sun continuously illuminated reference is approximately:

\[
G_{\mathrm{PV}}\approx C D \eta_{opt}
\]

before accounting for concentration-dependent PCE, temperature, degradation, and electrical losses.

For example, \(C=3\), \(D=0.5\), and \(\eta_{opt}=0.9\) gives:

\[
G_{\mathrm{PV}}\approx1.35
\]

so the same instantaneous system power would nominally require about:

\[
\frac{1}{1.35}=0.74
\]

times the PV area of the 1-sun continuous reference.

At \(C=3\), \(D=0.75\), and \(\eta_{opt}=0.9\):

\[
G_{\mathrm{PV}}\approx2.025
\]

corresponding nominally to about 49% of the PV area for the same instantaneous power.

These are system bookkeeping relationships, not evidence of a lifetime advantage. The lifetime advantage exists only if the controlled recovery schedule permits a favorable cumulative energy yield after degradation, thermal, optical, and mechanical penalties are included.

---

## 9. Adaptive angular-speed control

A preferred controller uses angular position feedback from an encoder and commands a nonuniform angular-velocity profile:

```text
ILLUMINATED SECTOR:
    choose ω_L from concentration, PV temperature,
    normalized power, recent dose and degradation state

DARK SECTOR:
    choose ω_D from estimated recovery benefit,
    temperature, cooling capacity and segment state

IF marginal recovery remains high:
    slow or dwell in dark sector

IF marginal recovery is low:
    accelerate toward next exposure

IF segment temperature approaches limit:
    shorten light exposure and/or extend dark dwell

IF output degradation exceeds expectation:
    increase recovery time, reduce concentration,
    change electrical operating point, or retire segment
```

The controller can update its empirical recovery model from measured response after each return to illumination.

Thus the apparatus can perform **online system identification**: it learns how much benefit a given segment actually obtains from a 1 s, 5 s, 30 s, or longer dark interval and adjusts future schedules accordingly.

---

## 10. Cloud, shade, eclipse, and interruption recovery

A drop in available sunlight can be used as a recovery opportunity rather than treated only as an external disturbance.

Examples include:

- passing terrestrial cloud;
- temporary shade;
- night;
- solar tracker repositioning;
- spacecraft eclipse;
- spacecraft attitude maneuver;
- temporary pointing error;
- deliberate power curtailment;
- maintenance or load shedding.

When irradiance falls below a controller-selected value, the system may:

1. slow or stop the rotor with selected segments in a dark/cooling region;
2. prioritize recovery of the most degraded, hottest, or most heavily dosed segments;
3. electrically decouple, short, open-circuit, or otherwise place segments into a calibrated recovery electrical state;
4. increase cooling while production opportunity is low;
5. redistribute subsequent exposure toward segments having the highest predicted recovered performance;
6. reduce subsequent concentration temporarily when illumination returns;
7. equalize state of health across segments.

When high irradiance returns, the controller can resume with the segments having the highest recovery score instead of blindly returning to a fixed angular schedule.

---

## 11. Electrical operating state during darkness

Darkness need not imply only “zero light.”

The electrical state of a dark segment may itself be controlled. Disclosed dark/recovery states include:

- electrical open circuit;
- short circuit;
- high-impedance isolation;
- controlled voltage bias;
- controlled current bias;
- temporary disconnection from MPPT;
- connection to a diagnostic impedance-measurement circuit;
- connection to a low-energy probing circuit;
- periodic health measurement before re-entry into concentrated illumination.

A dark electrical state may be selected independently for each segment or group of segments.

The purpose is to empirically identify which combination of optical darkness, temperature, and electrical boundary condition produces the highest future lifetime-energy return.

---

## 12. Thermal control

### 12.1 Short-time heat spreading

The rotating carrier acts as a thermal spreader and buffer. With a thin photovoltaic stack on a conductive carrier, the thermal mass that receives a short illumination pulse can be much larger than the perovskite layer itself.

The preferred system therefore minimizes thermal resistance between the active layer and the carrier while maintaining required electrical insulation.

### 12.2 Steady-state heat rejection

The carrier does not eliminate heat. In continuous operation, average absorbed optical power not converted to electricity must eventually be rejected.

Terrestrial embodiments can use:

- water or glycol cooling;
- liquid microchannels;
- forced air;
- evaporative systems;
- hybrid PV/thermal heat recovery.

Space embodiments can use:

- conductive heat straps;
- heat pipes;
- pumped loops;
- two-phase loops;
- radiator panels;
- high-emissivity surfaces;
- thermal storage for transient loads.

In vacuum, darkness alone is not cooling. Heat must ultimately be rejected radiatively or transferred to a radiator.

### 12.3 Avoiding damaging temperature cycling

A preferred embodiment deliberately keeps the PV layer near a controlled mean temperature while switching illumination on and off. The dark interval is not necessarily intended to return the segment to ambient temperature.

This distinction is important because published work has shown that large repeated temperature swings can create cyclic lattice strain and accelerate degradation in some perovskite architectures.

---

## 13. Segment architecture

The rotating surface may be continuous or segmented.

Possible embodiments include:

- continuous circumferential perovskite layer with distributed collection electrodes;
- axial strips;
- circumferential strips;
- rectangular cell tiles;
- independently addressable sectors;
- interleaved materials optimized for different concentration levels;
- redundant spare sectors;
- different perovskite compositions on different sectors for lifetime comparison or environmental adaptation.

Electrical power may be transferred by:

- slip rings;
- brushes;
- rotary electrical connectors;
- inductive/contactless transfer;
- on-rotor DC/DC conversion with rotary transfer at a common bus;
- commutated stationary contacts that engage only selected angular positions.

Some of these techniques are already known in rotating PV prior art and are included here as implementation alternatives, not as assertions of novelty.

---

## 14. Belt, reel, and long-recovery embodiments

The rotating drum is not the only implementation.

If a particular perovskite composition benefits from dark recovery lasting minutes or tens of minutes, the active surface can be a flexible endless loop routed through a compact reel magazine.

The loop may operate analogously to a continuous film transport:

```text
concentrated exposure
        ↓
thermal extraction
        ↓
dark recovery path / reel magazine
        ↓
optional health measurement
        ↓
return to concentrated exposure
```

If one frame is illuminated for \(t_L\) and must remain away from the illumination zone for \(t_D\), the required PV inventory relative to the currently illuminated PV area is approximately:

\[
\frac{A_{\mathrm{total}}}{A_{\mathrm{illuminated}}}
=
\frac{t_L+t_D}{t_L}
\]

The optical focus can remain continuously occupied because successive segments enter the illuminated zone while previously illuminated segments travel through the recovery path.

This embodiment is relevant where perovskite film mass and stowed volume are low enough that additional PV inventory is preferable to high degradation or large stationary receiver area.

---

## 15. Terrestrial embodiment

For terrestrial operation, the economic question is not whether concentration creates additional solar energy; it does not.

Potential advantages are instead:

- reduced simultaneously illuminated active PV area;
- use of low-cost optical aperture with smaller active perovskite receiver;
- controlled operating temperature;
- recovery scheduling;
- potentially increased lifetime energy per unit PV material;
- use of cloudy periods for recovery;
- optional capture of reject heat in a PV/T system.

A terrestrial system may be unattractive if optics, tracking, cooling, and mechanics cost more than simply deploying additional stationary PV area. Therefore the relevant terrestrial metric is lifetime energy cost, not peak power density alone.

---

## 16. Space embodiment

The concept may be more attractive where mass, stowed volume, radiation environment, and available receiver geometry dominate cost.

A space implementation can comprise:

- lightweight reflective collector aperture;
- compact rotating perovskite receiver;
- thermal path through the rotor shaft;
- heat pipes or pumped loop;
- spacecraft radiator;
- radiation-tolerant motor, bearings, and electronics;
- adaptive recovery scheduling during eclipse and attitude maneuvers.

Concentration does not reduce the optical aperture required to collect a given quantity of sunlight. It can, however, reduce the simultaneously active receiver area and permit the receiver material to be cycled through a controlled thermal and recovery environment.

The space case must separately account for vacuum, ultraviolet exposure, proton/electron radiation, atomic oxygen in low Earth orbit, thermal cycling, outgassing, and lubrication/bearing choices.

---

## 17. Minimum experimental program

The central claim should be treated as **unproven until the following experiment is completed**.

### Stage A — no mechanics

Use nominally identical perovskite cells on a temperature-controlled stage.

Minimum groups:

| Group | Irradiance | Light / dark schedule |
|---|---:|---|
| A | 1× | continuous |
| B | 3× | continuous |
| C | 3× | 270 s / 30 s |
| D | 3× | 90 s / 30 s |
| E | 3× | 30 s / 30 s |
| F | 3× | 10 s / variable dark |
| G | 2× | best schedule from C–F |
| H | 4× | best schedule from C–F |

Temperature should be held as constant as practicable across continuous and cycled tests so that light/dark recovery is not confused with large thermal cycling.

Measure:

- MPP power;
- PCE;
- \(V_{OC}\);
- \(J_{SC}\);
- fill factor;
- surface/cell temperature;
- cumulative incident dose;
- cumulative electrical energy;
- T95, T90, and T80 where test duration allows;
- recovery after selected dark intervals;
- cycle-to-cycle change in recovery magnitude.

Primary metric:

\[
E_{T80}=\int_0^{T80}P(t)\,dt
\]

Secondary metric:

\[
\text{dose}_{T80}
=
\int_0^{T80}G(t)\,dt
\]

The rotating architecture is justified only if the cycled/concentrated regime provides enough additional lifetime-energy or other system-level benefit to pay for the extra PV inventory and mechanics.

### Stage B — rotary bench prototype

Only after Stage A identifies a useful recovery law:

- 100–200 mm diameter thermally conductive drum;
- 8–32 logical PV segments;
- stepper/servo motor with encoder;
- calibrated lamp or solar simulator;
- adjustable concentrator;
- temperature sensors;
- irradiance sensor;
- current/voltage measurement;
- controlled coolant;
- programmable angular-velocity map.

The prototype should reproduce the best static-shutter schedule from Stage A using actual physical rotation.

### Stage C — outdoor adaptive control

Add real solar variability.

Compare:

1. fixed RPM;
2. temperature-only control;
3. irradiance + temperature control;
4. irradiance + temperature + recovery-history control.

The hypothesis is supported only if controller (4) produces a reproducible improvement in lifetime energy or another declared system metric.

---

## 18. Example adaptive algorithm

For each segment \(i\):

```text
measure irradiance I
measure/estimate segment temperature T_i
measure segment-normalized electrical response Pnorm_i
update cumulative dose Q_i
update state-of-health estimate H_i
update empirical recovery estimate R_i

if segment is illuminated:
    if T_i > thermal_limit:
        accelerate out of illuminated zone
    elif predicted degradation cost > predicted power benefit:
        shorten current exposure
    else:
        continue exposure

if segment is dark:
    estimate marginal recovery benefit dR/dt
    if dR/dt > recovery_threshold:
        remain longer in dark region
    else:
        make segment eligible for re-exposure

if ambient irradiance falls sharply:
    enter opportunistic recovery mode
    prioritize hottest / least-recovered / most-dose-loaded segments

when irradiance returns:
    expose the segment with the highest expected
    future-energy score, subject to thermal and mechanical limits
```

A more advanced controller can use model predictive control, Bayesian optimization, reinforcement learning, or a simpler lookup table derived from calibration data.

Machine learning is optional. The essential disclosed feature is **history-aware recovery control**.

---

## 19. Failure modes and design constraints

The concept can fail even if short-term recovery is observed.

Critical failure modes include:

1. **Thermal-cycle fatigue** — darkness causes large cooling and repeated lattice strain.
2. **Recovery benefit too small** — dark intervals do not sufficiently improve lifetime energy.
3. **Recovery is composition-specific** — a schedule that helps one perovskite harms another.
4. **Mechanical fatigue** — curved or flexible cells crack or delaminate.
5. **Encapsulation fatigue** — repeated strain or rotation compromises moisture/oxygen barriers.
6. **Electrical-contact wear** — slip rings or brushes become a dominant reliability issue.
7. **Optical loss** — concentrator losses consume the material-saving advantage.
8. **Tracking cost** — concentrator needs accuracy that is uneconomic.
9. **Hot spots** — nonuniform focused illumination creates local irreversible degradation.
10. **Cooling parasitics** — pump and radiator requirements overwhelm the PV advantage.
11. **Control instability** — adaptive scheduling chases short-term recovery while accelerating long-term damage.
12. **Motor/bearing reliability** — especially important in vacuum or remote terrestrial operation.
13. **Space thermal rejection** — concentrated receiver heat must still reach a radiator.
14. **No lifetime-energy gain** — the decisive negative result.

---

## 20. Prior-art boundary

This disclosure deliberately separates known architecture from the narrower combination being placed into the public technical record.

### 20.1 US 3,383,246 and US 4,211,581

Earlier solar conversion prior art describes a photoelectric converter associated with a solar concentrator in which the converter is rotated so that it periodically leaves the irradiation zone for cooling. US 4,211,581 explicitly describes this earlier arrangement as operating the light converter in a pulsed mode with cooling intervals.

**Therefore not new here:**

- rotating a PV converter;
- moving it out of a concentrated irradiation zone;
- cooling during intervals outside that zone;
- pulsed PV exposure as a cooling technique.

### 20.2 US20130008488A1 — rotating PV cells under concentration

This publication is particularly close. It discloses PV cells around rotating members, concentrated and non-concentrated illumination, cooling by rotation, internal heat-transfer fluid, heat sinks, heat pipes, slip rings, continuous/variable/start-stop rotation, and indexed control to optimize power output or cooling for different solar intensity levels.

**Therefore not new here:**

- cylindrical/rotating PV receiver;
- concentrated focal region;
- internal fluid cooling;
- variable RPM merely to control temperature;
- start/stop rotation merely to optimize power/cooling;
- slip-ring extraction;
- broad use with thin-film PV.

### 20.3 CN115039245A/B — printable curved perovskite solar cell

This family discloses printable perovskite photovoltaic structures on curved conductive substrates and expressly includes cylindrical surfaces.

**Therefore not new here:**

- perovskite merely being formed on a cylindrical or curved substrate.

### 20.4 WO2021144085A1 family — perovskite control in darkness / low irradiance

This family discloses a perovskite PV module whose electrical operating condition changes when irradiance falls below a predetermined threshold. Irradiance can be determined from PV photocurrent, an additional photocell, impedance spectroscopy, or estimated from meteorological data.

**Therefore not new here:**

- recognizing darkness/weak light as a special operating condition for perovskite;
- sensing irradiance;
- changing the electrical state when irradiance is low;
- using meteorological information as an irradiance input.

### 20.5 Scientific literature on perovskite concentration and light/dark cycling

Published work demonstrates that:

- perovskite cells can operate under concentrated illumination, including substantially above 3 suns;
- brief dark intervals can alter ion-mediated degradation and improve average device behavior in some tested cells;
- the useful amount of dark time is material- and age-dependent;
- excessive or thermally coupled cycling can be harmful because repeated temperature-driven lattice strain can accelerate degradation.

### 20.6 Residual combination intentionally disclosed here

The narrower combination placed into the public record by this document is:

> **A concentrated perovskite photovoltaic system in which physically movable PV segments are tracked individually or by groups using a recovery/degradation state derived from illumination history, dark history, dose, temperature and electrical performance, and in which movement, dwell, concentration, electrical state and/or cooling are adaptively scheduled to maximize predicted lifetime energy rather than merely instantaneous power or temperature.**

Further disclosed refinements include:

- nonuniform angular speed by angular region;
- empirical marginal-recovery optimization;
- online learning of the recovery curve;
- opportunistic recovery during cloud/shade/eclipse/pointing interruptions;
- state-of-health balancing among multiple perovskite segments;
- selection of the next illuminated segment according to recovery history;
- deliberate suppression of temperature amplitude while still providing optical darkness;
- combined mechanical dark cycling and electrical recovery-state control.

These features are disclosed regardless of whether they ultimately satisfy patent-law novelty or inventive-step requirements.

---

## 21. Disclosure variants intended to prevent narrow design-around

The following variants are explicitly contemplated:

1. drum, belt, reel, disk, polygon, carousel, wheel, loop, chain, or reciprocating carrier;
2. continuous or segmented perovskite layer;
3. one or multiple concentrators;
4. one or multiple illuminated zones;
5. one or multiple dark zones;
6. constant, variable, indexed, intermittent, bidirectional, or angular-position-dependent speed;
7. direct perovskite-on-carrier fabrication or attached flexible modules;
8. active liquid cooling, passive conduction, heat pipe, thermosyphon, pumped loop, radiator, or hybrid combinations;
9. terrestrial, airborne, marine, orbital, lunar, planetary, or deep-space use;
10. fixed concentration or controller-variable concentration;
11. fixed duty cycle or controller-variable duty cycle;
12. individual-segment health tracking or group/aggregate tracking;
13. deterministic controller, lookup-table controller, adaptive controller, optimization controller, model-predictive controller, or learned controller;
14. cloud/shade/eclipses treated as recovery events;
15. darkness combined with controlled open-circuit, short-circuit, isolated, biased, or diagnostic electrical states;
16. recovery scheduling based on cumulative dose rather than elapsed time alone;
17. recovery scheduling based on marginal recovery rather than complete recovery;
18. deliberate unequal use of segments to preserve reserve capacity;
19. retirement or bypass of degraded segments;
20. periodic recalibration of each segment’s recovery response.

---

## 22. What would falsify the concept

The concept should be abandoned or substantially narrowed if controlled experiments show that:

- at equal temperature and equal cumulative absorbed dose, light/dark cycling does not improve lifetime energy at useful concentration;
- repeated cycling causes greater irreversible degradation than continuous operation;
- the recovery benefit requires so much dark time that required PV inventory and mechanism dominate system mass/cost;
- concentration-dependent degradation overwhelms recovery benefit;
- thermal management cannot hold temperature cycling to an acceptable amplitude;
- required optical and tracking hardware costs more than additional stationary PV area in the target market;
- moving electrical/thermal interfaces cannot meet required reliability.

A negative result is useful: it prevents investment in a mechanically elaborate architecture whose only apparent benefit comes from short-term reversible recovery.

---

## 23. Current technical conclusion

The broad mechanical architecture is not novel.

The experimentally unresolved and potentially valuable question is:

\[
\boxed{
\text{Can controlled dark recovery under moderate concentration increase}
\quad
\frac{E_{\mathrm{life}}}{A_{\mathrm{PV}}}
\text{ or }
\frac{E_{\mathrm{life}}}{m_{\mathrm{system}}}
\quad
\text{enough to justify the moving receiver?}
}
\]

The strongest version of the concept is therefore not “a rotating perovskite solar cylinder.”

It is:

> **A history-aware, adaptive operating system for concentrated perovskite photovoltaics that physically schedules each photovoltaic region between generation and recovery states according to measured or inferred material recovery kinetics, while controlling temperature to avoid harmful thermal-fatigue cycling.**

The first decisive experiment requires no rotating hardware. Once a useful recovery law is measured, the drum, reel, or belt becomes an implementation of that law.

---

## 24. References and identified prior art

1. **US20130008488A1** — *Use of rotating photovoltaic cells and assemblies for concentrated and non-concentrated solar systems.* Priority 2011-07-07.  
   https://patents.google.com/patent/US20130008488A1/en

2. **US4211581A** — *Solar photoelectric conversion apparatus with cooling means.* Published 1980. Its background describes earlier US3383246 as a rotating light converter that periodically leaves the irradiation zone for cooling.  
   https://patents.google.com/patent/US4211581A/en

3. **US3383246** — *Rotatable solar energy converter.* Referenced as prior art by US4211581.  
   https://patents.google.com/patent/US3383246

4. **CN115039245A / CN115039245B** — *Printable curved surface perovskite solar cell and preparation method thereof.* Priority 2020-12-17.  
   https://patents.google.com/patent/CN115039245A/en

5. **WO2021144085A1 / EP3852145 / related family** — *Decoupling of a perovskite solar cell in darkness.* Priority 2020-01-15.  
   https://patents.google.com/patent/WO2021144085A1/en

6. Wang, Z. et al. **High irradiance performance of metal halide perovskites for concentrator photovoltaics.** *Nature Energy* 3, 855–861 (2018). Peak 23.6% at 14 suns; encapsulated devices retained >90% of initial efficiency after 150 h at 10 suns at MPP.  
   https://doi.org/10.1038/s41560-018-0220-2

7. Gillespie, S. C. et al. **Excitation Intervals Enhance Performance in Perovskite Solar Cells.** *ACS Applied Materials & Interfaces* 17, 59476–59485 (2025). Reports beneficial light/dark cycling in tested devices, including 270 s light / 30 s dark and evidence that useful dark intervals can be on the order of seconds; results are composition-, age-, and condition-dependent.  
   https://doi.org/10.1021/acsami.5c18736

8. Shen, Y. et al. **Strain regulation retards natural operation decay of perovskite solar cells.** *Nature* 635, 882–889 (2024). Shows that temperature-coupled day/night cycling can accelerate degradation through cyclic lattice strain, while cycled illumination at fixed temperature did not show the same accelerated decay.  
   https://doi.org/10.1038/s41586-024-08161-x

9. Huan, Z. et al. **Advancements in radiation resistance and reinforcement strategies of perovskite solar cells in space applications.** *Journal of Materials Chemistry A* 12, 1910–1922 (2024).  
   https://doi.org/10.1039/D3TA06388G

10. **EPO Article 54 / Guidelines — state of the art.** Publicly available written disclosures can form part of the state of the art; an enabling disclosure should contain enough information for a skilled person to put the teaching into practice.  
    https://www.epo.org/en/legal/epc/2020/a54.html  
    https://www.epo.org/en/legal/guidelines-epc/2026/g_iv_2.html

---

## 25. Publication record

When publicly publishing this disclosure, record:

- public repository URL;
- commit hash;
- UTC publication timestamp;
- immutable archive URL if available;
- document SHA-256;
- version number;
- author identity or stable pseudonymous identity if desired.

**Do not backdate the public disclosure date.** The relevant defensive-publication date is the date the technical content actually becomes publicly accessible.

