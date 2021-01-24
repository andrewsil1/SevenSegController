SevenSegController - AXI-compatible Seven Segment LED controller, with multiple configuration options
This design implements a flexible AXI4LITE interface to control seven-segment LED displays with several register-controlled features, including:
  * Parametric number of display digits from 1 to 8, which can be set at design time.  Defaults to 8 to match the Digilent Nexys4 series boards.
  * 32-bit control register, addresses 00-03:
  *  Bit 0: Display in hexadecimal format when 0, display in decimal format when 1
  *  Bit 1: Trim leading zeroes from display when 1.  Display all digits when 0.
  *  Bits 2-6 reserved
  *  Bit 7: Master Enable.  Set to 1 to enable display, set to 0 to turn off all digits.
  *  Bits 8-31 reserved
  
  * 32-bit data register, addresses 04-07: Value to be displayed
  
  * Decimal point display implemented via 8-bit bitfield (32-bit register 2 least significant byte, addresses 0x8-0xB)
  * When the display is being used in decimal mode, exceeding the highest displayable decimal value for the number 
  of available digits will result in ALL decimal points being lit to indicate overflow.  In that case, only the 
  least significant digits are actually displayed.
  
