This is a fork of the [Intan RHX software](https://github.com/Intan-Technologies/Intan-RHX), up-to-date with the version 3.0.5 of the main branch.

This is an unofficial fork with some additions compared to the official software:
- the introduction of a post-microstimulation blanking windows where the highpass filtered traces are forced to 0 to prevent large artifact-induced signal and false detection of spikes
- the spike detection threshold based on the RMS of the channels has been replaced by a median-based threshold as [proposed by Quian Quiroga et Al. (2004)](http://www.scholarpedia.org/article/Spike_sorting#Step_ii.29_Spike_Detection)

# Intan-RHX

Intan RHX is free, powerful data acquisition software that displays and records electrophysiological signals from any Intan RHD or RHS system using an RHD USB interface board, RHD recording controller, or RHS stim/recording controller.

# Original instruction on how to run the software

## All Platforms:

Various files need to be present in the same directory as the binary executable at runtime. These include
* kernel.cl
* ConfigRHDController.bit
* ConfigRHDInterfaceBoard.bit
* ConfigRHSController.bit
* ConfigXEM6010Tester.bit
* USBEvaluationBoard.bit.

### Windows:

The RHX software depends on Opal Kelly USB drivers and Microsoft Redistributables. When running the distributed Windows installer from the Intan website, these are automatically installed, but when building RHX from source, these should still be installed on the system. Opal Kelly USB drivers should be installed so that the Intan hardware can communicate via USB. These are available at: https://intantech.com/files/Intan_controller_USB_drivers.zip. These also rely on the Microsoft Visual C++ Redistributables (x64) from 2010, 2013, and 2015-2019, which are available from Microsoft and should also be installed prior to running IntanRHX. Finally, okFrontPanel.dll (found in the libraries directory) should be in the same directory as the binary executable at runtime.

### Mac:

libokFrontPanel.dylib should be in a directory called "Frameworks" alongside the MacOS directory within the built IntanRHX.app. Running macdeployqt on this application will also populate this directory with required Qt libraries.

### Linux:

A udev rules file should be added so that the Intan hardware can communicate via USB. The 60-opalkelly.rules file should be copied to /etc/udev/rules.d/, after which the system should be restarted or the command 'udevadm control --reload-rules' should be run. libokFrontPanel.so should be in the same directory as the binary executable at runtime. 
