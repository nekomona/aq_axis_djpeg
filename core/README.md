# JPEG Decoder Core

![jpegd](docimg/jpegd.png)

Original author: [aquaxis](https://github.com/aquaxis)
Bug fixes and improvements: [nekomona](https://github.com/nekomona)

## Introduction

This core is a JPEG Decoder for the JPEG baseline decoder with streaming input and blocked stream output.
Designed for decoding basic types of JPEG images as well as the first layer of progressive JPEGs.

The information of JPEG, including image size, baseline or progressive and color components are automatically extracted from the header of JPEG stream. JPEG data stream will be accepted through a FIFO input interface, while pixel stream and pixel position stream extracted through a FIFO output interface.

## Features

- ISO/IEC 10918-1 compliant JPEG Baseline decoding
- Up to 64K x 64K image resolution
- Dynamic quantization tables and Huffman tables
- Automatic JPEG header extractor for tables and image properties
- Supporting YCbCr 4:4:4, YCbCr 4:2:2H, YCbCr 4:2:2V, YCbCr 4:2:0 and monochrome inputs
- Supporting extraction on the first layer of progressive JPEG
- Supporting DRI label and restarts
- Peak performance at 1clk/pixel

## Limitations

- Up to 2 8-bit Quantization Tables
- Up to 4 Huffman Tables (2 for DC, 2 for AC)
- Image SOF are required to be aligned with 4B boundary
- Only 1(Monochrome) or 3(YCbCr) image component types supported
- Corrupted frames are not supported
- Following layers of progressive JPEG are ignored
- 32 bit aligned input format

## Resource Utilization

| Device   | fACLK  | fTCLK  | LUT  | FF   | BRAM | DSP  |
| -------- | ------ | ------ | ---- | ---- | ---- | ---- |
| 7A100T-1 | 100MHz | 100MHz | 4580 | 4353 | 6    | 13   |

Synthesized and implemented with default config in Vivado 2018.3

