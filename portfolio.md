# About me

I am a software engineer specialising in developing control systems for scientific applications, these systems consist of a Python backend, a RESTful API and a React based webapp user facing interface. I have had over two and a half years experience delivering these systems for the Science and Technology Facilities Council (STFC), these sytems have been used in production environments at the Diamond Light Source.

My work usually builds on that of our in-house firmware team, or on the SDK of a device manufacturer to allow scientific users to efficiently and effectively operate complex instruments. I take full ownership of the development cycle from requirements gathering with clients to deployment and long-term support, usually involving working closely with multidisciplinary teams.

# Featured Projects

## GPIB Device Control System 
**Dates:**  Sep 2022 - Jan 2023

**Tech Stack:** Python 3, HTML/JS, PyVisa, RaspberryPi, Linux

**Purpose/Context:** Developed a control system for Keithley Instruments high-voltage power supplies and thermoelectric cooler controllers to allow remote operation and monitoring from outside the experiment hutch, contributing to massively reducing experiment downtime during beaming experiments at Diamond Light Source.

**Approach** 
- Designed Python classes to represent a generic GPIB device that provided the basic communication protocols over PyVisa and used inheritance to build device specific classes to represent distinct Kiethley Instrument models
- Made use of threading locks to manage which device could use the PyVisa Protocol at once due to its limitation of using a single channel for communication to all connected devices.
- Implemented device discovery, enabling support for up to 15 connected instruments with dynamic instantiation of device classes and generation of API endpoints and UI components.

**Outcomes:**
- successfully deployed for scientific applications at Diamond Light Source, and routinely used on beamline experiments, API used to integrate the system into other control systems.
- Reduced downtime on beaming experiments by reducing the need for manual intervention in radiation controlled areas.

**Example of the UI:**
  <img width="1917" height="452" alt="image" src="https://github.com/user-attachments/assets/7534c2b3-f601-4563-8ec2-08fac803d0b2" />


## PicoScope Data Acquisition (DAQ) and Control System 
**Dates:**  Jan 2023 - Oct 2023

**Tech Stack:** Python 3, HTML/JS, picoSDK, Linux

**Purpose/Context:** Created a control and data acquisition system for a PicoScope digital oscilloscope used in material characterisation, allowing for live examining of data, along with recording traces to HDF5 files. 

**Approach** 
- Developed test capture scripts to characterise capture performace using the picoSDK in python, and determine if Python was a suitable langauge to use for the DAQ system.
- Designed Python classes to manage distinct components of the DAQ system, such as a file writing, data buffer management, PicoScope device representation. Implemented Python dataclasses to seperate the system configuration from the implementation code.
- Used tools such as Doxygen to auto-generate documentation on the code layout for incoming apprentices to work on the project. 

**Outcomes:**
- Successfully deployed for material characterisation at STFC, regularly used by in-house scientists along with external users from Cambridge University.  
- Project picked up by apprentices for additional features and improvements.

**Example of the UI:**
<img width="1913" height="899" alt="pico-odin" src="https://github.com/user-attachments/assets/5b360586-5f00-4f46-8683-1035bbf9a8f5" />

## Jupyterhub Service Usage Metrics 
**Dates:**  Oct 2023 - Apr 2024

**Tech Stack:** Python 3, Django, Prometheus, Kubernetes, Linux

**Purpose/Context:** Extended the existing JASMIN metrics service to include tracking the usage statistics of a Jupyterhub service deployed for external scientific users. This included tracking the number of active containers running and the resources they were using.  

**Approach** 
- Used kubernetes and Helm Charts to configure and deploy a test Jupyterhub environment to develop on without affecting the user service.
- Developed simple Django views to gather metrics off the Jupyterhub deployment and expose them on an API that was formatted as Prometheus Gauges. Established Prometheus scrape jobs to regularly store the usage metrics into the JASMIN metrics database. Created Grafana graphs and charts to plot the metrics gathered.
- Developed unit testing for the views with Python Mocking/Patching to test the views with previous good API responses, integrated the unit tests into JASMINS GitLab CI/CD pipline for automatic testing when new commits are made to the repository. 

**Outcomes:**
- Successfully investigated the possible solutions for gathering metrics on the Jupyterhub deployment, allowing for tracking of users of the service, and the system resources being used.    
- Additional Django views deployed and data fed into existing Metrics monitoring system.

## DynamiX Detector Control System 
**Dates:**  Apr 2024 - Feb 2025

**Tech Stack:** Python 3, ZeroMQ, React, Linux

**Purpose/Context:** Integrated multiple subsystem API's for the Dynamix expiermental detector into one single control system, enabling operators to manage all relevant system components from one interface during beamline experients.  

**Approach** 
- Created python dataclasses to map subsystem parameters onto, to create interfaces that could be used to interact with individual subsystem API's from within Python. 
- Implemented a state machine to control the data acqusition process and control several subsystems at once. 
- Developed Live read-out system to retrieve live data coming off the detector, enabling the scientific users to make real time adjustments to system paramemters.

**Outcomes:**
- Successfully deployed control system to Diamond Light Source Beamline experiments, with the system being used to ooperate the DyanamiX Detector system and capture data.     
- Control system allowed less tehcnically trained staff to operate the detector due to the simplified interface. 

## DSSG Monitoring Package
**Dates:** Feb 2025
**Tech Stack:** Python 3, Prometheus, Linux

**Purpose/Context:** Developed a plugin-based monitoring system to export performance, utilisation, and environmental metrics for machines in the STFC DSSG labs, supporting sustainability initiatives. The system helps identify high power usage or low utilisation systems, and correlates this with environmental data such as lab temperature to assess when air conditioning systems are triggered — enabling data-driven adjustments to reduce overall power consumption.

**Approach:**
- Created a modular Python package providing a Prometheus-cient http server, and designed a dyanmic "collector" loading system, allowing for metrics to be sourced from other python files without having to be part of the Monitoring package, to allow for easy use of user-written collectors.
- Setup the package with modern standard pyproject.toml allowing for optional dependencies to be specified for each collector and allowing the user to only install the python libraries they need.
- Worked closely with an Apprentice to direct improvements to the package, commenting on their pushes to the codebase, providing code reviews and completing pull requests with them to introduce new functionality to the package.
- Fed data into a prometheus database and grafana views to create dashboard showing the different metrics.

**Outcomes:**
- Successfully developed an inital prototype of the system, and worked closely with an Apprentice to bring out the full functionality.
- Package deployed to ten's of machines to feed different metrics back into the database about the usage of our systems in the Labs. 
