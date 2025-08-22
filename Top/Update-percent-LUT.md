# Enhanced-percent-LUT

I would like to create a new feature/ branch on 'moku-dev-vhdl' and 'moku-dev-python' called 'enhanced-percent-LUT'

## Enhanced LUT description.

Our first iteration of a percent LUT defined the following datatype
![[moku-dev-vhdl/common/percent_lut_pkg.vhd]]


I would like to enhance it to:
* append Include a simple CRC to the end of the LUT
* I would also like a (simple) python script that can read and write LUTs. 

For now the python utilities should be able to read and write
- `.bin` files (raw binary) 

Ask follow up questions.