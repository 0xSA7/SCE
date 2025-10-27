# 2 Data Link Layer

- Physical layer transmits raw bits but cannot handle errors, noise, or flow control.
- Data Link Layer provides reliable device-to-device transfer using error detection/correction and flow control.
- Sender: receives Network-layer data, adds control fields (addresses, checks, sequence numbers) to form a frame, and passes it to the Physical layer.
- Receiver: converts signals to bits, verifies/removes control fields, corrects or discards errors, and forwards valid data to the Network layer.

### 2.2.1 Service Provided by Data Link Layer

- Terminology:
    - DL-SDU (Data Link Service Data Unit): user data from the Network layer.
    - DL-PDU (Data Link Protocol Data Unit): frame formed by adding header/trailer to the DL-SDU.
- Basic service: reliable transfer of DL-SDUs over a data link connection established, maintained, and released on request from the Network layer.
- Associated features:
    - Sequencing: preserves order and integrity of DL-SDUs.
    - Error Notification: reports unrecoverable errors to the Network layer.
    - Flow Control: regulates the rate at which the sender accepts DL-SDUs.
    - QoS Parameters: selectable options such as residual error rate, transit delay, and throughput.

### 2.2.2 Data Link Protocols

- Both ends must agree on frame structure and procedures to identify control fields and exchange control information.
- Data link protocol: the set of rules/procedures for data link control functions.
- Protocol specifications:
    - Frame format: locations and sizes of fields.
    - Field contents: information carried in each field.
    - Message sequence: order of control/data messages for error and flow control and management.
- Examples: BISYNC (BSC), SDLC, HDLC, ADCCP, PPP.

## 2.3 Frame Design Considerations

- General frame format: Header (control fields) — Data (user information) — Trailer (control fields).
### 2.3.1 Types of Frame Formats
    - Variable format — variable length.
    - Fixed format — fixed length.
    - Fixed format — variable length.
- Purpose: enable receiver to find frame start, identify fields, and separate the data field.

### 2.3.2 Transparency
- Service must allow arbitrary user data; mechanisms are needed to prevent user data from being misinterpreted as delimiters or control identifiers.

### 2.3.3 Bit-Oriented vs. Byte-Oriented Protocols
- Bit-oriented: control information encoded at the bit level; data field length need not be a multiple of bytes (e.g., HDLC).
- Byte-oriented: control information encoded at the byte level; data field size is a multiple of bytes (e.g., BISYNC).
