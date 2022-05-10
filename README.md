CheapSk8 LAN is an 8-bit ISA network card based on the RTL 8019AS chip.  

This project was created for cost savings over purchasing older cards on eBay or building other similar projects.

By sourcing the MagJack and RTL8019AS from Aliexpress, the 93LC46 from eBay, and the discretes from Mouser or Digikey, and the PCB from JLCPCB, the bill of materials for a board is only about $7.50 when you build 20 or more.

Link to MagJacks: https://www.aliexpress.com/item/32845892783.html

Link to RTL8019AS: https://www.aliexpress.com/item/4000545658898.html

Link to 93LC46 SMT 1k PROM: https://www.ebay.com/itm/133483822518

Entire project is licensed under CC BY-SA 4.0: https://creativecommons.org/licenses/by-sa/4.0/  You may copy/modify/distribute this project as you see fit as long as my name and project name are listed, and the license is carried forward to your project.


Drivers / Configuration:

In the Drivers/Config folder, you will find the following software:

NE2000.COM - Modified Crynwr Packet Driver for 8-bit NE2000 based cards.  Modified by Dan over on the VCF Forums (https://forum.vcfed.org/index.php?threads/ne2000-packet-drivers-for-8-bit-slots.41507/)
NE2000.ASM - Associated file to NE2000.COM
PG9018.EXE - Initial programming tool for the card.
8019AS.CFG - Initial Configuration file for the card (Read ahead carefully)
RSET8019.EXE - Configuration tool for the card.

Before configuration, edit 8019AS.CFG and add a MAC address to the 1st line.  If you are building more than one card, you should ensure that no two cards have the same address.  You can use one of the Private MAC address Allocations, known as "Locally Administered Address Ranges" and will not be used by mainstream devices or vendors. The MAC addresses in these ranges can be safely used, as long as they are unique within your network:

x2-xx-xx-xx-xx-xx
x6-xx-xx-xx-xx-xx
xA-xx-xx-xx-xx-xx
xE-xx-xx-xx-xx-xx

Each pair can be any hexadecimal number. You use space instead of - in the cfg file.  For example:  52 0a 1b 3c 4e 5f 00 or 12 1a 2b 3c 4d 5e

You should set your IOBASE to a free IO address (300 is default), IRQ (2 is default), and enable or disable the bootrom.  Beware conflicts with XT-IDE, or certain Sound Card/Midi Devices.  

Once you have edited the file to your liking, boot your machine with no memory managers (EMM386 or HIMEM.sys) and run PG8019.EXE  - this will program the card and tick up the MAC address and serial number incrementally in the 8019as.cfg file, so you don't have to edit to run it on subsequent cards.

Once the card is programmed, you can use RSET8019.EXE at any time to change the Base address and IRQ if you plan to change your system configuration.


