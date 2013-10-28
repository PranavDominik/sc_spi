.. _sec_api:

SPI master API
==============

.. _sec_conf_defines:

Configuration defines
---------------------

The file spi_conf.h can be provided in the application source code, without it 
the default values specified in spi_master.h and spi_slave.h will be used.
This file can set the following defines:

**DEFAULT_SPI_CLOCK_DIV**

    This define sets the default clock divider, which the application can use 
    when initializing the SPI master. See **spi_clock_div** parameter of 
    ``spi_master_init()`` in :ref:`sec_conf_functions` for clock divider format.
    Leave this set at 2 for the maximum SPI clock frequency of 25 MHz.

**SPI_MASTER_MODE**

    The SPI mode the master operates in.
    
    +------+------+------+
    | Value| CPOL | CPHA |
    +======+======+======+
    |   0  |   0  |   0  |
    +------+------+------+
    |   1  |   0  |   1  |
    +------+------+------+
    |   2  |   1  |   0  |
    +------+------+------+
    |   3  |   1  |   1  |
    +------+------+------+

SPI master API
--------------

Data Structures
+++++++++++++++
.. doxygenstruct:: spi_master_interface

.. _sec_conf_functions:

Configuration Functions
+++++++++++++++++++++++
.. doxygenfunction:: spi_master_init
.. doxygenfunction:: spi_master_shutdown

Receive Functions
+++++++++++++++++
.. doxygenfunction:: spi_master_in_byte
.. doxygenfunction:: spi_master_in_short
.. doxygenfunction:: spi_master_in_word
.. doxygenfunction:: spi_master_in_buffer

Transmit Functions
++++++++++++++++++
.. doxygenfunction:: spi_master_out_byte
.. doxygenfunction:: spi_master_out_short
.. doxygenfunction:: spi_master_out_word
.. doxygenfunction:: spi_master_out_buffer


