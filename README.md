# Zynq Notes

## Overview

This page documents some notes for using Zynq devices. The notes are tested against Digilent, using a mix of Vivado 2022/2023.

## Notes

To start, create a new Zynq hardware project.

Navigate to the block design, and add a "Zynq7 Processing System" IP. Right click and run block automation:

!(zynq7 processing system added)[rsrc/1_zynq7ps.png]

Right click the block diagram in the Sources window, and select "Create HDL Wrapper":

!(hdl wrapper)[rsrc/3_hdlwrap.png]

Right click the processing system, go to Peripheral I/O Pins, navigate to UART1 and select an appropriate IO port (over the USB cable, MIO 48/ MIO 49 on UART 1):

!(uart1 port select)[rsrc/AXI_UART_Zynq.png]

Generate the bitstream, go for a walk, and once it's done, click File - Export Hardware. Make sure to select the option to include the bitstream:

!(export hardware)[rsrc/4_export_hdl.png]

This will create a file with an "XSA" extension.

Now, run the "Vitis" application. Make sure you are running Xilinx Vitis 2022. Make sure you're running "Xilinx Vitis", and not the completely different "Vitis", it should open into something like this:

!(vitis)[rsrc/5_vitis.png]

In Vitis, go to "File/New/Application Project". When you select your platform, click the "Create a new platform from hardware (XSA)" tab. Click next, and add the details for your application project:

!(vitis again)[rsrc/6_app_project.png]

Fill in both the "Application project name" and "System project name". Select "hello world" to populate a skeleton application.

The Zybo board multiplexes UART with JTAG over USB, so you'll need to use special settings to talk properly. This is the Tera Term configuration (default config):

!(tera term)[rsrc/tera_term.png]

## References

- https://digilent.com/reference/learn/programmable-logic/tutorials/zedboard-getting-started-with-zynq/start
- https://www.hackster.io/dhq/getting-started-with-the-minized-fpga-soc-aa7a25
