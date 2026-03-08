# Communication protocols

| Layer             | Description                                           |
| ----------------- | ----------------------------------------------------- |
| Network Layer     | Transfers bits a bytes                                |
| Transport layer   | Controls that bits and bytes are transferred properly |
| Application Layer | Makes REST API calls and sends emails                 |

List of protocols:

- **Application Layer (Layer 7)**:
  - `HTTP` (Hypertext Transfer Protocol): Stateless Request Response Cycle
  - `HTTPS`: Secure HTTP
  - `SMTP`: Email Transfer Protocol
- **Transport Layer (Layer 4)**:
  - `TCP` (Transimission Control Protocol): Realiability > Performance
  - `TLS` (Transport Layer Security): Secure TCP
  - `UDP` (User Datagram Protocol): Performance > Reliability
- **Network Layer (Layer 3)**:
  - `IP` (Internet Protocol): Transfer bytes. Unreliable.

Each layer makes use of the layers beneath it: application layer > transport layer > network layer.

> [!IMPORTANT]
> Most applications talk at application layer, but some applications talk through network layer directly (for high performance).
