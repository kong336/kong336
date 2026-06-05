# keyl / kong336

I build small embedded and vision systems, then turn the lab notes into repositories that can be tested, deployed, and reused.

Right now my main focus is a drone-side perception bridge:

- NVIDIA Jetson Xavier NX for camera capture, TensorRT YOLO inference, depth sampling, HTTP preview, and UDP JSON output.
- STM32MP257 / OpenSTLinux for receiving vision packets, polling fallback HTTP, parsing UWB/AOA frames, and running a monitor-only mission state machine.
- Safety-first integration: dry-run state transitions, MAVLink heartbeat checks, schema validation, and local replay tests before any actuator control.

## Current Projects

[drone-vision-bridge](https://github.com/kong336/drone-vision-bridge)  
Jetson-to-STM32MP257 vision bridge with TensorRT YOLO, Orbbec depth, UWB/AOA parsing, MAVLink heartbeat probing, systemd deployment notes, and offline test coverage.

[embedded-contest-kit](https://github.com/kong336/embedded-contest-kit)  
Competition-oriented embedded C starter pack with portable modules and STM32 HAL adapters.

[embedded-notes](https://github.com/kong336/embedded-notes)  
Official-source-first embedded systems learning notes and resource maps.

## Working Areas

- Embedded Linux: OpenSTLinux, systemd services, networked board bring-up.
- Edge vision: Jetson Xavier NX, YOLOv8, TensorRT, camera/depth pipelines.
- MCU and firmware: STM32, C, HAL-style adapters, serial protocols.
- Robotics plumbing: UDP contracts, UWB/AOA, MAVLink heartbeat checks, dry-run state machines.
- Engineering hygiene: readable docs, reproducible tests, clear deployment runbooks.

## Current Direction

I am building toward a bench-validated drone manipulator stack where each layer is testable on its own:

```text
camera/depth -> Jetson inference -> UDP/latest.json -> MP257 state machine -> dry-run arm decision
```

The near-term goal is not to hide rough experiments. It is to make each experiment easier to rerun, inspect, and improve.