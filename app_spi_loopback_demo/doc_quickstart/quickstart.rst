SPI master/slave loopback example application: quick start guide
================================================================

This simple demonstration of xTIMEcomposer Studio functionality uses the xCORE Simulator together with the xSOFTip ``module_spi_slave`` and ``module_spi_master`` to demonstrate the SPI slave. This demo application demonstrates the SPI slave xSOFTip by connecting it to our SPI master xSOFTip. The SPI master runs in one logical core, with its ports looped back to ports used by the SPI slave xSOFTip, running on the same xCORE tile, in a second logical core. Before running this demo application, it is recommended that you familiarize yourself with the simulator, see :menuitem:`Help, Tutorials, xTIMEcomposer Studio Tutorial`.

Hardware setup
--------------

This application only requires the xCORE Simulator software to run.

The simulator can be run either from within xTIMEcomposer Studio, or using the xSIM command-line tool.

Import and build the application
--------------------------------

#. Open xTIMEcomposer Studio.
#. Open the edit perspective by selecting :menuitem:`Window, Open Perspective, XMOS Edit`.
#. Locate the ``SPI Master/Slave Loopback Example Application`` item in the xSOFTip pane on the bottom left of the window, and drag it into the Project Explorer window in the xTIMEcomposer.
#. This will also cause the modules on which this application depends to be imported as well.
#. This application depends on:
    * module_spi_master
    * module_spi_slave
#. Click on the app_spi_loopback_demo item in the Explorer pane then click on the build icon (hammer) in xTIMEcomposer.
#. Check the console window to verify that the application has built successfully.

For help in using xTIMEcomposer, try the xTIMEcomposer tutorial, which you can find by selecting :menuitem:`Help, Tutorials` from the xTIMEcomposer menu.

Note that the Developer Column in the xTIMEcomposer on the right hand side of your screen provides information on the xSOFTip components you are using. Select a module in the Project Explorer, and you will see its description together with API documentation. Having done this, click the `back` icon until you return to this quickstart guide within the Developer Column.

Run the application
-------------------

Now that the application has been compiled, the next step is to run it on the xCORE Simulator.

#. Select the file ``spi_loopback_demo.xc`` in the ``app_spi_loopback_demo`` project from the Project Explorer.
#. Create a basic Run Configuration for the simulation using these `instructions <https://www.xmos.com/node/14798#xde-simulate-program-run-conf/>`_, but do not click ``Run`` yet.
#. Set up a loopback, using these `instructions <https://www.xmos.com/node/14798#set-up-a-loopback>`__, between the following pins:

    - ``from: Tile=tile[0], Port=XS1_PORT_1A, Offset=0, Width=1``
    - ``to:   Tile=tile[0], Port=XS1_PORT_1B, Offset=0, Width=1``
    - ``from: Tile=tile[0], Port=XS1_PORT_1C, Offset=0, Width=1``
    - ``to:   Tile=tile[0], Port=XS1_PORT_1D, Offset=0, Width=1``
    - ``from: Tile=tile[0], Port=XS1_PORT_1E, Offset=0, Width=1``
    - ``to:   Tile=tile[0], Port=XS1_PORT_1F, Offset=0, Width=1``
    - ``from: Tile=tile[0], Port=XS1_PORT_1G, Offset=0, Width=1``
    - ``to:   Tile=tile[0], Port=XS1_PORT_1H, Offset=0, Width=1``

#. Enable signal tracing on the loopback pins, using these `instructions <https://www.xmos.com/node/14798#trace-a-signal>`__ to trace the ports on Tile[0].
#. Click ``Run`` to start the simulation.

The output to the console should show the SPI mode and frequency, the number of tests the demo will perform, and then the result of each test as follows::

  Running in SPI mode 3
  with SPI frequency 25MHz
  for 3 demo runs
  Demo run 1
  All data returned from slave received correctly
  Demo run 2
  All data returned from slave received correctly
  Demo run 3
  All data returned from slave received correctly

To view the trace of the SPI signals, open ``app_spi_loopback_demo.vcd`` and select the signal for each of the ports setup in the loopback. Displaying these signals should result in the waves being in the Waves view. The ports map to the SPI signals as follows, as can be seen in ``spi_master_interface`` and ``spi_slave_interface`` structs declared in ``spi_loopback_demo.xc``:

.. list-table::
    :header-rows: 1

    * - SPI Signal
      - MOSI
      - MISO
      - SCLK
      - SS
    * - SPI Master
      - PORT_1A
      - PORT_1C
      - PORT_1E
      - PORT_1G
    * - SPI Slave
      - PORT_1B
      - PORT_1D
      - PORT_1F
      - PORT_1H

.. only:: latex

    .. figure:: images/waves-wide.*
       :width: 120mm

       Waves view showing SPI loopback traces

.. only:: html

    .. figure:: images/waves.*

       Waves view showing SPI loopback traces

Next steps
----------

#. Examine the application code. In xTIMEcomposer Studio navigate to the ``src`` directory under app_spi_loopback_demo and double click on the ``spi_loopback_demo.xc`` file within it. The file will open in the central editor window.
#. Trying changing the SPI mode or frequency in ``spi_conf.h``, and inspect the changes to the loopback signal traces after rerunning the simulation.

Try related applications
------------------------

#. app_spi_master_demo

