# Bachelor's thesis and Internship OSCAR uHasselt 

---

![OSCAR logo](../Images/OSCAR_Logo_NoBg.png)

# Title
Development of an FPGA-based data acquisition and control system for quantum diamond magnetometers

## Abstract

An FPGA-based data acquisition and control subsystem is designed, implemented, and partially validated for integration into the OSCAR EduQUBE quantum diamond magnetometer demonstrator, advancing the throughput and timing capabilities of the existing microcontroller-FGPA-based readout toward nanosecond-deterministic hardware execution and faster data acquisition times.
Nitrogen-vacancy (NV) centers in diamond enable room-temperature quantum sensing of magnetic fields through Optically Detected Magnetic Resonance (ODMR). The EduQUBE, developed by the OSCAR research group at Hasselt University, makes this technology accessible for education and space-oriented research — including Earth's magnetic field mapping, rocket trajectory sensing, and navigation applications. The current platform relies on a microcontroller for readout and signal processing, but sequential execution, interrupt latency, and limited data throughput constrain the timing precision and signal-to-noise ratio achievable during NV-center measurements.
The FPGA subsystem is organized into four protocol-agnostic IP subsystems — sensor interface, measurement, memory, and digital signal processing — communicating over standardized AXI-Stream and start/busy/done interfaces, drawing on architectural insights from master theses within the OSCAR group. The DSP subsystem implements a moving average filter, FIR low-pass filter, decimator, and a full IQ lock-in amplifier. The lock-in amplifier is thoroughly validated in simulation through targeted test cases covering frequency selectivity, phase invariance, realistic ODMR lineshapes including single Lorentzian dips and hyperfine triplets, and mathematical verification against a first-principles theoretical derivation — confirming its readiness for real-time ODMR demodulation on hardware.
Key subsystem paths were verified in hardware as standalone circuits, including QSPI communication from an STM32 through to the FPGA interface controller and an end-to-end ADC readout chain validated using an externally generated test signal. A first measurement of the raw ODMR data was also comfirmed working, however, lack of synchronization options between the FPGA setup and the actual EduQUBE prevented testing the DSP pipeline on an actual ODMR signal.
As quantum sensing matures toward deployment in space instrumentation, geomagnetic surveying, and precision navigation, accessible and well-documented platforms such as the EduQUBE play an important role in bridging research-grade quantum instrumentation and the next generation of engineers working in these fields.



---