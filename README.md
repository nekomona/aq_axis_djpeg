### AXI-4 JPEG Decoder

Github:   [https://github.com/ultraembedded/legacy_jpeg_decoder](https://github.com/ultraembedded/legacy_jpeg_decoder)

This component is a HW JPEG decoder (in Verilog) with AXI-4 DMA.  
Based around [aquaxis](https://github.com/aquaxis) JPEG decoder core.

#### Features
* HW JPEG decoder.
* AXI-4 lite configuration interface.
* AXI-4 DMA for JPEG fetch, and RGB data writeback.
* RGB565 output format.
* ISO/IEC 10918-1 compliant JPEG Baseline decoding.
* Up to 64K x 64K image resolution.
* Dynamic quantization tables and Huffman tables.
* Automatic JPEG header extractor for tables and image properties.
* Supporting YCbCr 4:4:4, YCbCr 4:2:2H, YCbCr 4:2:2V, YCbCr 4:2:0 and monochrome inputs.
* Supporting extraction on the first layer of progressive JPEG.
* Supporting DRI label and restarts.

##### Register Map

| Offset | Name | Description   |
| ------ | ---- | ------------- |
| 0x00 | JPEG_CTRL | [RW] JPEG Control Register |
| 0x04 | JPEG_STATUS | [R] Status Register |
| 0x08 | JPEG_SRC | [RW] DMA Source Address |
| 0x0c | JPEG_DST | [RW] DMA Target Address |

##### Register: JPEG_CTRL

| Bits | Name | Description    |
| ---- | ---- | -------------- |
| 31 | START | Start transfer. |
| 30 | ABORT | Abort transfer. |
| 23:0 | LENGTH | Source buffer length in bytes. |

##### Register: JPEG_STATUS

| Bits | Name | Description    |
| ---- | ---- | -------------- |
| 0 | BUSY | Core busy. |

##### Register: JPEG_SRC

| Bits | Name | Description    |
| ---- | ---- | -------------- |
| 31:0 | ADDR | Address (must be 32-byte aligned). |

##### Register: JPEG_DST

| Bits | Name | Description    |
| ---- | ---- | -------------- |
| 31:0 | ADDR | Address |

#### Testing
Tested on a Xilinx Artix 7 (Digilent Arty A7).

#### References
* [aquaxis](https://github.com/aquaxis)  
* [nekomona](https://github.com/nekomona)
