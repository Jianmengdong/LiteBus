# LiteBus
An IPbus-like hardware control bus.
Currently using 8 bits address length and 48 bits data length.
--------------------------------------------------
Request packet:
    63   60 |59       57| 56 |55      48 |47   0
     header |  trans ID | R/W| address   | data
--------------------------------------------------
Header: b'0100
Trans ID: from 1 to 7, increase by 1 after each transaction
R/W: '1' for write, '0' for read
address: 8 bits support 256 registers in total; can be extended by adding length
data: payload data to write to a register; ignored when R/W is '1'
--------------------------------------------------
Responde packet:
    63   60 |59       57| 56 |55      48 |47   0
     header |  trans ID | 0  | address   | data
--------------------------------------------------
Header: b'0100
Trans ID: same with the request; if not, error ocurred
address: same with the request
data: the register value
