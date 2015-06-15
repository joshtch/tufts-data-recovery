###################
# SMART Self-test #
###################

Running the test
----------------

All modern hard drives come with SMART (Self-Monitoring,
Analysis and Reporting Technology) software/firmware for self-analysis.
On Linux, the tool used to run SMART is called `smartctl` (SMART ConTroL),
part of the `smartmontools` package.

To start a quick test, use the following command, replacing `sdx` with the
relevant device identifier.

  # smartctl --test=short -d sat /dev/sdx

The `-d sat` part tells smartctl the drive is a SATA device.
As always, refer to the manpage if you're not sure about anything
or if you want to learn more.

After two minutes, the test should be finished. To see the results:

  # smartctl -A -f brief -d sat /dev/sdx

I'll often open a new terminal window and run the following, so I don't have
to remember to run it later. This will run the command automatically after
a 2-minute wait:

  $ sleep 2m; sudo smartctl -A -f brief -d sat /dev/sdx


Interpreting the results
------------------------

Note that the attributes printed will vary by vendor. So the output displayed
will be different for Seagates and Western Digitals, for example. The values
in particular to look for, though, are the same. In order of importance, they
are:

  ID #198: `Offline Uncorrectable`,  
  ID #5 or #196: `Reallocated Sector Count`  
  ID #197: `Current Pending Sector`

If any of these have a `RAW_VALUE` greater than zero, the drive has started to
fail. 

So, for instance, with the following output

    smartctl 6.4 2014-10-07 r4002 [x86_64-linux-3.16.0-4-amd64] (local build)
    Copyright (C) 2002-14, Bruce Allen, Christian Franke, www.smartmontools.org
    
    === START OF READ SMART DATA SECTION ===
    SMART Attributes Data Structure revision number: 10
    Vendor Specific SMART Attributes with Thresholds:
    ID# ATTRIBUTE_NAME          FLAGS    VALUE WORST THRESH FAIL RAW_VALUE
      1 Raw_Read_Error_Rate     POSR--   114   099   006    -    70618491
      3 Spin_Up_Time            PO----   093   086   000    -    0
      4 Start_Stop_Count        -O--CK   100   100   020    -    410
      5 Reallocated_Sector_Ct   PO--CK   100   100   036    -    4
      7 Seek_Error_Rate         POSR--   053   053   030    -    3659501202650
      9 Power_On_Hours          -O--CK   035   035   000    -    57607
     10 Spin_Retry_Count        PO--C-   100   100   097    -    13
     12 Power_Cycle_Count       -O--CK   100   037   020    -    391
    184 End-to-End_Error        -O--CK   100   100   099    -    0
    187 Reported_Uncorrect      -O--CK   100   100   000    -    0
    188 Command_Timeout         -O--CK   100   098   000    -    4295032838
    189 High_Fly_Writes         -O-RCK   100   100   000    -    0
    190 Airflow_Temperature_Cel -O---K   065   043   045    Past 35 (0 12 36 28 0)
    194 Temperature_Celsius     -O---K   035   057   000    -    35 (0 10 0 0 0)
    195 Hardware_ECC_Recovered  -O-RC-   036   016   000    -    70618491
    197 Current_Pending_Sector  -O--C-   100   100   000    -    0
    198 Offline_Uncorrectable   ----C-   100   100   000    -    0
    199 UDMA_CRC_Error_Count    -OSRCK   200   200   000    -    0
                                ||||||_ K auto-keep
                                |||||__ C event count
                                ||||___ R error rate
                                |||____ S speed/performance
                                ||_____ O updated online
                                |______ P prefailure warning
    

the important ones are:

    ---
      5 Reallocated_Sector_Ct   PO--CK   100   100   036    -    4
    ---
    197 Current_Pending_Sector  -O--C-   100   100   000    -    0
    198 Offline_Uncorrectable   ----C-   100   100   000    -    0
    ---

The reallocated sector count is 4 (last column), so this drive is in the early
stages of failure. 


Running the Long Test
---------------------

Even if all four values are zero, the drive could still be failing. If the
short test didn't find anything, try the long test.

  # smartctl --test=long -d sat /dev/sdx

The results are interpreted the same way as for the short test.
