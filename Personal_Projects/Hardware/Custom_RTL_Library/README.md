# FPGA Custom RTL Library

---

<table border="0">
  <tr>
    <td align="center">
      <img src="../Images/FPGA_IPs.png" width="500px">
    </td>
    <td>
      Throughout the past 3 years (2023-2026), my main focus has been around FPGA design, and more specifically RTL design. My focus on FPGA development led to a vast amount of research, experimentation, numerous prototypes, actual designs (of which a small amount is mentioned in this portfolio) and a custom library of IPs.
      The attractiveness of this custom RTL IP library is the full  ownership, which gives full control over properties like  determinism,  latency, resource and power usage. Alongside this,  vendor independency is created too a large degree, which allows  for immediate migration between different hardware and development  tools with relative ease.  
      Where applicable, IPs are implemented to have proper protocol  agnosticity and clearly seperated control and data paths. For  example, most streaming IPs are chosen to implement the AXI stream  protocol, as it is widely used, but the custom nature of the RTL  provides the opportunity to modify the IP to implement other  protocols.  
      As a side note, and as this library is an ongoing work of progess  not all IPs are fully implemented to include all possible  functionalities. Throughout the development of this library,  choices where made to deliberately leave out functionality or  implementing only the necessary parts at the time due to time  constraints. However, in those cases, the remaining  functionalities that did not make it in the current implementation  are to be added  with relative ease.  
      This IP library will not be open-sourced as some parts of it  are used in private or production projects. However, i'm open for  contact and discussing collaborations or contributions on a  contract / freelance base.  
      As to give an idea what can be found in this IP library, a slight  overview is given below. 
    </td>
  </tr>
</table>

---

<table border="0">
  <tr>
    <td>
      <table >
        <tr>Primitives:</tr>
        <tr>- Multiplexers: MUX (a)sync</tr>
        <tr>- Buffers: FIFO</tr>
        <tr>- Shift registers: SIPO, PISO, PIPO, ...</tr>
        <tr>- Counter / timer / PWM</tr>
        <tr>- Pulse / strobe generator</tr>
        <tr>- ROM / Dual port RAM</tr>
      </table>
    </td>
    <td align="center">
      <img src="../Images/MUX.png" width="100%">
    </td>
  </tr>
</table>

---

<table border="0">
  <tr>
    <td align="center">
      <img src="../Images/SPI.png" width="100%">
    </td>
    <td>
      Communication:
      - UART
      - I2C
      - SPI / QSPI
      - PS/2
      - VGA
      - Line encodings
    </td>
  </tr>
</table>

---

<table border="0">
  <tr>
    <td><img src="../Images/CDC.png" width="100%"></td>
    <td>
      Clock Domain Crossing:
      - FlipFlop sync
      - Pulse stretch sync
      - CDC handshake bridge
      - Async FIFO (cummings architecture) 
    </td>
  </tr>
</table>


<table border="0">
  <tr>
    <td align="center">
      <img src="../Images/DSP_Lockin_Amp.png" width="100%">
    </td>
    <td>
      Digital Signal Processing
      - RGB to Grayscale
      - Audio: volume, delay, distortion,...
      - Average / moving average
      - FIR Low Pass Filter
      - Lock-in amplifier
    </td>
  </tr>
</table>

---

<table border="0">
  <tr>
    <td>
      Control IPs
      - Interface controller
      - Register map 
    </td>
  <tr>
  <tr>
    <td><img src="../Images/Controller.png" width="100%"></td>
  </tr>
</table>
