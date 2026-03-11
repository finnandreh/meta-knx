# TODO

## Planned Tasks

### [ ] Plan WSL-Based Embedded Simulation and Instance-Cloning System
Status: `queued`
Priority: `high`
Created: `2026-03-11`
Type: `architecture/implementation plan (no full code yet)`

#### Copilot Instruction
Plan a WSL-based development architecture that supports both:

1. simulation/prototyping of embedded devices inside WSL before real hardware exists
2. isolated per-run WSL instances created from a local base image copy and started with a separate instance name

Target domain: an embedded distributed system using ESP32-class devices, where some parts may later run on real hardware, but early development must support simulation and prototyping inside WSL.

#### Main goals
- simulate or prototype device behavior inside WSL
- allow multiple virtual device instances to run in isolation
- support a repeatable workflow for cloning a local WSL base image
- launch new WSL instances with unique names
- keep simulation state isolated per instance
- allow later migration from simulated devices to real ESP32 firmware or hybrid test setups

#### Required planning scope
1. Device simulation layer
- simulated device processes
- role-based node instances
- virtual GPIO/state abstractions
- simulated message passing
- optional CAN/message-bus abstraction
- optional mock wireless behavior
- deterministic test scenarios
- state-machine testing
- transition path toward real firmware and hardware
- practical host-side simulation over full hardware-perfect emulation
- optional future ESP-IDF/QEMU integration where useful

2. WSL base-image and cloning layer
- one prepared master/base WSL environment
- export or image-based snapshot strategy
- creation of local copies for new runs
- mandatory creation sequence for every new runnable instance:
  - start a fresh source instance
  - create an image/export copy with a proper target name
  - remove the original source image/instance
  - start only the newly copied instance
- import/start of cloned instances
- unique instance naming
- per-instance workspace separation
- cleanup/rebuild strategy
- reproducible startup flow

3. Instance orchestration layer
- instance registry
- naming rules
- launch rules
- status inspection
- log access
- stop/restart/remove operations
- mapping between instance name and simulated system role
- ability to launch one or many device groups

4. Development workflow layer
- create a new prototype environment
- start a new isolated WSL simulation instance
- assign a role to the instance
- run one or more simulated devices
- connect devices logically
- preserve or discard instance state
- evolve from simulation to real hardware

#### Required outputs for the plan
1. Purpose
2. System goals
3. Architecture overview
4. Layer decomposition
5. WSL image strategy
6. Clone-and-launch workflow
7. Instance naming scheme
8. Simulated device model
9. Process model for virtual nodes
10. Communication model between simulated nodes
11. File/folder structure
12. Scripts and tooling plan
13. Validation strategy
14. Migration path to real ESP32 devices
15. Risks and limitations
16. Recommended first prototype

#### Important constraints
- do not assume full hardware-perfect ESP32 emulation is required at first
- prefer practical simulation of device behavior and protocols over unrealistic full emulation
- keep the design modular so real ESP32 firmware can later replace or coexist with simulated nodes
- treat WSL instance cloning and naming as a first-class system feature
- keep reproducibility and isolation central to the design
- keep the plan implementation-oriented, not theoretical
- enforce this lifecycle for new instances: start source instance -> copy image with proper name -> remove original image -> start copied image

#### Also include in the future deliverable
- suggested file structure for:
  - base-image management
  - WSL clone/import scripts
  - simulated device definitions
  - orchestration scripts
  - logs
  - configs
  - test scenarios
  - future firmware integration
- suggested script responsibilities for:
  - create-base-image
  - clone-instance
  - start-instance
  - stop-instance
  - destroy-instance
  - launch-simulation
  - assign-role
  - list-instances
  - run-test-scenario
- scaling strategy for:
  - multiple simulated rooms
  - multiple controller roles
  - hybrid real/simulated environments
  - CI-based scenario testing
  - firmware-in-the-loop evolution

#### Final instruction for execution time
Produce a practical architecture and implementation plan only.
Do not generate the full code yet.
Focus on a design that is realistic to build incrementally inside WSL.
