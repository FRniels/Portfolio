# FPGA RTL Trivium Encryption

---

<table border="0">
  <tr>
    <td align="center">
      <img src="../Images/Trivium_cipher.png" width="100%">
    </td>
    <td>
      This project concludes the development of an FPGA RTL encryption IP. On suggestion by one of my teachers F. Vreys, the encryption cipher of choice is the Trivium synchronous stream cipher.
    </td>
  </tr>
</table>

---

The hardware design consists out of the components which can be seen in the blockdesign. The design mainly exists out of a 4 subsystems: Processing Unit, VDMA, Trivium encryption/decryption and UART Tx.
As this  is just a proof of concept, the processing unit stores a fixed ASCII string in DDR and configures the VDMA for this address range. The VDMA is also configured to operate in a circular buffer mode, thus repeating the same fixed ASCII string. The choice of VDMA over  normal DMA is used as this design will eventually be used as the basis for audio and video encryption. However, a normal DMA version is also included in the Vivado project. The Trivium top IP will encrypt the data received from the VDMA, immediately decrypts it, and finally sends it out over UART for verification. In real applications, the encryption and decryption IPs will of course be implemented on seperate devices.

![Blockdesign](../Images/Trivium_cipher_block_design.png)

The following image is a simulation snapshot from the simulation files included inside the Vivado process. The major thing to focus on is the generation of the key bit stream, which is XOR'ed with the raw data to enctypt, and with the encrypted data to decrypt. In the simulation it should be noted that the encryption and decryption process use the identical key bit stream, thus the decrypted data should equal the raw data before encryption.

![Simulation](../Images/Trivium_Simulation.png)

## Github repository
[Github repository](https://github.com/Fre101/FPGA_Encryption_Trivium)

---

# Reflection

## Korthagen Reflection Model

### Action

During this project, a teacher mentioned having briefly encountered the Trivium stream cipher during his master studies but never deeply explored it beyond a quick skim of a KU Leuven paper. As someone with a strong interest in FPGAs and raw RTL design, I took on the challenge of implementing Trivium in pure RTL.

I began by thoroughly reading the KU Leuven paper as well as an additional paper I found independently. Using the pseudocode described in the first paper as a basis, I constructed the actual RTL implementation. One notable design decision was dividing the cipher's internal state registers into clean 32-bit segments rather than grouping them in three large registers as the paper suggests. While this approach appeared more timing-friendly at first glance, I did not benchmark it at higher clock speeds to confirm whether it genuinely improves timing closure. A side effect of this choice was that the initialization code became harder to read.

For the test setup, the eventual goal of this IP is video encryption. However, to start, a small fixed ASCII string was used as test data: the string is sent, encrypted, decrypted, and printed over UART. This was sufficient to demonstrate the cipher in action. The physical setup consisted of a PYNQ-Z2 board, where the ARM processor initializes the DDR memory with the fixed string and configures a VDMA (Video DMA) to use that address range. The VDMA is configured in circular buffer mode, continuously streaming the data. The stream passes through the Trivium IP, which encrypts it, immediately decrypts it, and sends the result out over UART for verification. The full encryption and decryption process is clearly visible in the simulation waveforms.

### Looking Back

I genuinely enjoyed this project because it combined low-level hardware design with a concrete cryptographic application. Reading through the academic papers and translating pseudocode into synthesizable RTL was a satisfying challenge. Seeing the simulation correctly show the encrypt-then-decrypt flow confirmed that the core logic was working as intended.

The 32-bit register partitioning decision is something I reflect on with mixed feelings. It made intuitive sense from a timing perspective, but without actually testing it at higher clock frequencies I cannot confirm it was the right trade-off. The reduced readability of the initialization code is a concrete downside that I did notice during development.

If time had allowed, the ideal setup would have involved two separate devices: one for encryption and transmission, the other for reception and decryption. That would have made a much stronger proof of concept. The single-device loopback approach, while functional as a prototype, does not fully demonstrate the real-world use case.

### Awareness of Essential Aspects

This project taught me how important it is to map theoretical specifications — in this case academic pseudocode — onto hardware-friendly structures. The decision about register layout had real consequences for both timing and code clarity, and it illustrated that hardware design often involves trade-offs that are not obvious until implementation.

It also highlighted the value of simulation as a verification tool. Being able to see the encryption and decryption clearly in the waveform file made it much easier to validate the behavior of the IP without needing a full physical test environment with two separate boards.

### Creating Alternatives

If I were to redo this project, I would benchmark the 32-bit register partitioning against the original three-register grouping at multiple clock frequencies. This would give a data-driven answer to whether the chosen structure actually benefits timing, rather than relying on intuition.

I would also aim to set up the two-device test scenario from the start. Having a dedicated encryption device and a dedicated decryption device would produce a much more convincing demonstration and would more closely resemble the eventual video encryption use case.

### Trial

In future RTL projects, I will continue grounding my implementations in primary academic sources and will be more deliberate about documenting and validating design decisions — especially ones that affect both timing and code readability. I also plan to make two-device or end-to-end integration testing a standard part of my prototyping process rather than an afterthought.

---

## PXL X-Factor

* **(Em)passion:** I took on a cryptographic hardware challenge out of personal interest in RTL design, going beyond the material introduced in class to explore and implement an academic cipher from scratch.
* **Entrepreneurial:** I independently sourced a second academic paper to complement the KU Leuven paper and used both to build a complete, working IP core — taking the project further than what was formally required.
* **Innovative:** I designed a synthesizable Trivium stream cipher in pure RTL with a custom 32-bit register structure and integrated it into a full FPGA data pipeline using VDMA and UART on a PYNQ-Z2.
* **(Inter)nationality:** Working from international academic papers and applying their content to a practical embedded hardware project developed my ability to engage with technical literature from the broader research community.
* **Multi-perspective:** I considered both the hardware timing implications and the software readability impact of my register design choice, and reflected on how the prototype setup compares to a real-world two-device deployment scenario.

---

## Sustainable Development Goals (SDGs)

### SDG 4 – Quality Education

This project contributed to SDG 4 by demonstrating self-directed, research-driven learning. By reading and applying content from academic cryptography papers to build a working hardware implementation, I went beyond passive instruction and engaged with the kind of independent technical study that characterizes lifelong engineering education.

### SDG 9 – Industry, Innovation and Infrastructure

The project aligns with SDG 9 through the design of an innovative, reusable cryptographic IP core for FPGA. Stream ciphers such as Trivium are relevant to real-world applications including secure video transmission. Developing a scalable, hardware-efficient implementation of such a cipher reflects the kind of infrastructure-level innovation that supports secure digital communication systems.