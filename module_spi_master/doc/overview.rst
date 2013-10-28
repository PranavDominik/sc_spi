Overview
========

All four SPI modes (0 through 3 are supported) as shown below


SPI modes
---------

+------+------+------+
| Mode | CPOL | CPHA |
+======+======+======+
|   0  |   0  |   0  |
+------+------+------+
|   1  |   0  |   1  |
+------+------+------+
|   2  |   1  |   0  |
+------+------+------+
|   3  |   1  |   1  |
+------+------+------+

Performance
----------- 

The achievable clock speed and effective bandwidth varies according to which of the SPI modes is used, as shown below. This information has been obtained by testing on real hardware.

+------+----------------------------+------------------------------------------+
| Mode | Master SCLK freq [#first]_ | Master bandwidth (Read/Write) [#second]_ |
+======+============================+==========================================+
|   0  | 25MHz                      | 18.2Mbps / 5.1Mbps                       |
+------+----------------------------+------------------------------------------+
|   1  | 25MHz                      | Not tested                               |
+------+----------------------------+------------------------------------------+
|   2  | 25MHz                      | Not tested                               |
+------+----------------------------+------------------------------------------+
|   3  | 25MHz                      | 18.2Mbps / 17.8Mbps                      |
+------+----------------------------+------------------------------------------+

.. [#first] Maximum frequency with which tests could be completed correctly
.. [#second] The bandwidth was measured by running app_spi_master_demo on an XP-SKC-L2 -  
             writing a single 256byte page to the flash, and reading 50kB from it.

All bandwidth tests were conducted with the maximum supported SCLK frequency, unless otherwise stated. Where SCLK frequencies are given, these were found to be the maximum with which the tests could be completed correctly.

