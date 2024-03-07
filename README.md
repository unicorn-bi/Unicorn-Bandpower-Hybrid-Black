# Unicorn Bandpower Hybrid Black

[Starting Unicorn BandPower From the Unicorn Suite ](#starting-unicorn-bandpower-from-the-unicorn-suite)<br/>

[Status Bar](#status-bar)<br/>

[Control Bar](#control-bar)<br/>

[Main Page](#main-page)<br/>

[Settings](#settings)<br/>

[UDP Interface](#udp-interface)<br/>
    - [UDP Interface Payload Structure](#udp-interface-payload-structure)<br/>

[UDP Bandpower Receiver](#udp-bandpower-receiver)<br/>
    - [Requirements](#requirements)<br/>
    - [Files on your computer](#files-on-your-computer)<br/>
    
[Recordings](#recordings)<br/>

 Unicorn Bandpower Hybrid Black is an application allowing the user to visualize brainwaves from 8 positions on the head. Additionally, the bandpowers for delta (1-4 Hz), theta (4-8 Hz), beta low (12-16 Hz), beta mid (16-20 Hz), beta high (20-30 Hz) and gamma (30-50 Hz) are estimated continuously. The Unicorn Bandpower features an UDP interface allowing users to integrate bandpower features into their own applications. Bandpower features can also be stored in CSV files for offline processing.

<p align="center">
<img src="./img/UnicornBandPower.png" alt="drawing" width="500"/><br/>
</p>

## Starting Unicorn BandPower From the Unicorn Suite 
The Unicorn Bandpower can be started from the Unicorn Suite. The Unicorn Bandpower is listed in the Unicorn Suite in the “Apps” section. Before you can start Unicorn Bandpower, the application must be unlocked using the license manager. The Unicorn Bandpower is licensed with the same license feature as the Unicorn Recorder. The Unicorn must be paired before using it with Unicorn Bandpower. If the Unicorn is paired, the serial number of the device should be listed in the drop-down box in the Unicorn Suite. Select the serial number and press open, then start the Unicorn Bandpower with the selected device.

<p align="center">
<img src="./img/UnicornBandPowerStartMenu.png" alt="drawing" width="500"/><br/>
</p>

This dialog is displayed if the connection attempt failed. Make sure that the device is turned on and paired 
before using the Unicorn Bandpower.

<p align="center">
<img src="./img/UnicornBandPowerConnect.png" alt="drawing" width="500"/><br/>
</p>

## Status Bar
<p align="left">
<img src="./img/Statusbar.png" alt="drawing" height="30"/><br/>
</p>
The following table represents the icons available in the status bar in the upper right corner
<p align="center">
<img src="./img/StatusIndicator.png" alt="drawing" width="500"/><br/>
</p>

## Control Bar
<p align="left">
<img src="./img/Controlbar.png" alt="drawing" height="30"/><br/>
</p>

The following table represents the icons available in the control bar in the upper left corner
<p align="center">
<img src="./img/ControlbarDescription.png" alt="drawing" width="500"/><br/>
</p>

## Main Page
After connecting to a Unicorn, the user is directed to the main page. The main page features a scope for visualizing and analyzing EEG data. Data in the scope are filtered with a second order Butterworth bandpass filter ranging from 0.5 to 50 Hz. 
<p align="center">
<img src="./img/MainPage.png" alt="drawing" width="500"/><br/>
</p>
The signal quality scope provides feedback about the signal quality for each channel. Therefore, the root mean square values of each channel are observed and compared to the thresholds of proper EEG. If an electrode in the signal quality scope turns green, the electrode delivers proper EEG. No action is required. If an electrode in the signal quality scope turns red, the electrode is either floating or flatlined. In both cases, the electrodes do not provide proper EEG. These electrodes should be removed from the data acquisition. You can click on a channel in the signal quality plot to remove it from the data acquisition.
<p align="center">
<img src="./img/MainPage2.png" alt="drawing" width="500"/><br/>
</p>
The bandpower plot shows the estimated bandpower value for the defined frequency ranges. The defined frequency ranges are delta (1-4 Hz), theta (4-8 Hz), beta low (12-16 Hz), beta mid (16-20 Hz), beta high (20-30 Hz) and gamma (30-50 Hz). The bandpower for each channel is displayed if the “Channels” tab is selected. The average bandpower of all channels is displayed if the “Average” tab is selected. The average bandpower of all possible bipolar derivations of the channels is displayed if the “Bipolar” tab is selected. The update rate of this plot depends on the buffer setting defined in the settings dialog:

<p align="center">
<img src="./img/MainPage3.png" alt="drawing" width="500"/><br/>
</p>

<p align="center">
<img src="./img/MainPage3_1.png" alt="drawing" width="500"/><br/>
</p>

<p align="center">
<img src="./img/MainPage3_2.png" alt="drawing" width="500"/><br/>
</p>

## Settings
The Unicorn Bandpower application features a UDP interface. The IP address and port can be modified in the settings dialog. You can also enable or disable the UDP interface in this dialog. 
The sampling rate of the bandpower features depends on the buffer size and buffer overlap configuration. The sampling rate can be determined as follows:

$$ f_{Bandpower} =  { f_{Unicorn} \over buffer size - bufferoverlap} [Hz] $$

By default, the sampling rate of the Unicorn is 250 Hz, the buffer size of the bandpower buffer is 250 samples and the buffer overlap is set to 240 samples. These parameters result in a 25 Hz update rate of the bandpower features.

It is possible to modify the output path for file recordings as well as the filename of the recorded data file. Click the “Reset Defaults” button to restore the default configuration. 

<p align="center">
<img src="./img/MainPage4.png" alt="drawing" width="500"/><br/>
</p>

## UDP Interface

You can forward bandpower features using an UDP network protocol. The status bar shows the "?" icon if the UDP interface was enabled in the settings dialog. 
<p align="center">
<img src="./img/UDP1.png" alt="drawing" width="500"/><br/>
</p>

### UDP Interface Payload Structure
The user will always receive a payload consisting of 70 values structured as described below. Data are sent as a comma separated string in an ASCII format. If channels are disabled in the current data acquisition, the data values are replaced with NaN.

The bandpower feature payload sent via UDP is structured as following:

<p align="center">

| 1: delta<br>channel 1                                  | 2: delta<br>channel 2                                  | 3: delta<br>channel 3                                     | 4: delta<br>channel 4                                     | 5: delta<br>channel 5                                      | 6: delta<br>channel 6                                  | 7: delta<br>channel 7          | 8: delta<br>channel 8                                  |
| ------------------------------------------------------ | ------------------------------------------------------ | --------------------------------------------------------- | --------------------------------------------------------- | ---------------------------------------------------------- | ------------------------------------------------------ | ------------------------------ | ------------------------------------------------------ |
| 9: theta<br>channel 1                                  | 10: theta<br>channel 2                                 | 11: theta<br>channel 3                                    | 12: theta<br>channel 4                                    | 13: theta<br>channel 5                                     | 14: theta<br>channel 6                                 | 15: theta<br>channel 7         | 16: theta<br>channel 8                                 |
| 17: alpha<br>channel 1                                 | 18: alpha<br>channel 2                                 | 19: alpha<br>channel 3                                    | 20: alpha<br>channel 4                                    | 21: alpha<br>channel 5                                     | 22: alpha<br>channel 6                                 | 23: alpha<br>channel 7         | 24: alpha<br>channel 8                                 |
| 25: beta low<br>channel 1                              | 26: beta low<br>channel 2                              | 27: beta low<br>channel 3                                 | 28: beta low<br>channel 4                                 | 29: beta low<br>channel 5                                  | 30: beta low<br>channel 6                              | 31: beta low<br>channel 7      | 32: beta low<br>channel 8                              |
| 33: beta mid<br>channel 1                              | 34: beta mid<br>channel 2                              | 35: beta mid<br>channel 3                                 | 36: beta mid<br>channel 4                                 | 37: beta mid<br>channel 5                                  | 38: beta mid<br>channel 6                              | 39: beta mid<br>channel 7      | 40: beta mid<br>channel 8                              |
| 41: beta high<br>channel 1                             | 42: beta high<br>channel 2                             | 43: beta high<br>channel 3                                | 44: beta high<br>channel 4                                | 45: beta high<br>channel 5                                 | 46: beta high<br>channel 6                             | 47: beta high<br>channel 7     | 48: beta high<br>channel 8                             |
| 49: gamma<br>channel 1                                 | 50: gamma<br>channel 2                                 | 51: gamma<br>channel 3                                    | 52: gamma<br>channel 4                                    | 53: gamma<br>channel 5                                     | 54: gamma<br>channel 6                                 | 55: gamma<br>channel 7         | 56: gamma<br>channel 8                                 |
| 57: delta channel 1-8 averaged                         | 58: theta channel 1-8 averaged                         | 59: alpha channel 1-8 averaged                            | 60: beta low channel 1-8 averaged                         | 61: beta mid channel 1-8 averaged                          | 62: beta high channel 1-8 averaged                     | 63: gamma channel 1-8 averaged | 64: delta channel 1-8 bipolar derivations and averaged |
| 65: theta channel 1-8 bipolar derivations and averaged | 66: alpha channel 1-8 bipolar derivations and averaged | 67: beta low channel 1-8 bipolar derivations and averaged | 68: beta mid channel 1-8 bipolar derivations and averaged | 69: beta high channel 1-8 bipolar derivations and averaged | 70: gamma channel 1-8 bipolar derivations and averaged |                                |                                                        |
</p>

## UDP Bandpower Receiver

### Requirements
- NET Framework <br/> .NET Framework 4.8
- Visual Studio<br/> Microsoft Visual Studio 2022

### Files on your computer
By default, the Unicorn .NET API library is installed into the Documents folder.
- C:\Users\<username>\Documents\gtec\Unicorn Suite\Hybrid Black\Bandpower\ Bandpower UDP Receiver<br/>Standard installation folder for the Unicorn .NET API
library

The Unicorn Bandpower Receiver is an example of how to receive data from the Unicorn Bandpower UDP interface in C#. The application receives data from the Unicorn Bandpower application and prints received data to the console window. Users can create their own applications (e.g. neurofeedback applications) by using the UDP interface to get bandpower features.

## Recordings
During the acquisition, the user can press the record button to start or stop recordings to store data in a csv file. The csv file will always consist of 70 columns representing all 70 bandpower features. If channels are disabled or the feature can’t be evaluated, the values are replaced with NaN. 

The csv columns are structured as following:

<p align="center">

| 1: delta<br>channel 1                                  | 2: delta<br>channel 2                                  | 3: delta<br>channel 3                                     | 4: delta<br>channel 4                                     | 5: delta<br>channel 5                                      | 6: delta<br>channel 6                                  | 7: delta<br>channel 7          | 8: delta<br>channel 8                                  |
| ------------------------------------------------------ | ------------------------------------------------------ | --------------------------------------------------------- | --------------------------------------------------------- | ---------------------------------------------------------- | ------------------------------------------------------ | ------------------------------ | ------------------------------------------------------ |
| 9: theta<br>channel 1                                  | 10: theta<br>channel 2                                 | 11: theta<br>channel 3                                    | 12: theta<br>channel 4                                    | 13: theta<br>channel 5                                     | 14: theta<br>channel 6                                 | 15: theta<br>channel 7         | 16: theta<br>channel 8                                 |
| 17: alpha<br>channel 1                                 | 18: alpha<br>channel 2                                 | 19: alpha<br>channel 3                                    | 20: alpha<br>channel 4                                    | 21: alpha<br>channel 5                                     | 22: alpha<br>channel 6                                 | 23: alpha<br>channel 7         | 24: alpha<br>channel 8                                 |
| 25: beta low<br>channel 1                              | 26: beta low<br>channel 2                              | 27: beta low<br>channel 3                                 | 28: beta low<br>channel 4                                 | 29: beta low<br>channel 5                                  | 30: beta low<br>channel 6                              | 31: beta low<br>channel 7      | 32: beta low<br>channel 8                              |
| 33: beta mid<br>channel 1                              | 34: beta mid<br>channel 2                              | 35: beta mid<br>channel 3                                 | 36: beta mid<br>channel 4                                 | 37: beta mid<br>channel 5                                  | 38: beta mid<br>channel 6                              | 39: beta mid<br>channel 7      | 40: beta mid<br>channel 8                              |
| 41: beta high<br>channel 1                             | 42: beta high<br>channel 2                             | 43: beta high<br>channel 3                                | 44: beta high<br>channel 4                                | 45: beta high<br>channel 5                                 | 46: beta high<br>channel 6                             | 47: beta high<br>channel 7     | 48: beta high<br>channel 8                             |
| 49: gamma<br>channel 1                                 | 50: gamma<br>channel 2                                 | 51: gamma<br>channel 3                                    | 52: gamma<br>channel 4                                    | 53: gamma<br>channel 5                                     | 54: gamma<br>channel 6                                 | 55: gamma<br>channel 7         | 56: gamma<br>channel 8                                 |
| 57: delta channel 1-8 averaged                         | 58: theta channel 1-8 averaged                         | 59: alpha channel 1-8 averaged                            | 60: beta low channel 1-8 averaged                         | 61: beta mid channel 1-8 averaged                          | 62: beta high channel 1-8 averaged                     | 63: gamma channel 1-8 averaged | 64: delta channel 1-8 bipolar derivations and averaged |
| 65: theta channel 1-8 bipolar derivations and averaged | 66: alpha channel 1-8 bipolar derivations and averaged | 67: beta low channel 1-8 bipolar derivations and averaged | 68: beta mid channel 1-8 bipolar derivations and averaged | 69: beta high channel 1-8 bipolar derivations and averaged | 70: gamma channel 1-8 bipolar derivations and averaged |                                |                                                        |
</p>

<p align="center">
<img src="./img/DataExcel.png" alt="drawing" width="500"/><br/>
</p>

The update rate of the bandpower features depends on the buffer size and buffer overlap configuration as described in [Settings](#settings)