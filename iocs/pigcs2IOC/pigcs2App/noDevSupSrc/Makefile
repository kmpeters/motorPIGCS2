TOP=../..

include $(TOP)/configure/CONFIG
#----------------------------------------
#  ADD MACRO DEFINITIONS AFTER THIS LINE
#=============================

# The following are used for debugging messages.
#!USR_CXXFLAGS += -DDEBUG

#=============================
# Build the IOC application

PROD_IOC = pigcs2NoDevSup
# pigcs2NoDevSup.dbd will be created and installed
DBD += pigcs2NoDevSup.dbd

# pigcs2NoDevSup.dbd will be made up from these files:
pigcs2NoDevSup_DBD += base.dbd

# Include dbd files from all support applications:
#ifdef ASYN
pigcs2NoDevSup_DBD += asyn.dbd
pigcs2NoDevSup_DBD += drvAsynSerialPort.dbd
pigcs2NoDevSup_DBD += drvAsynIPPort.dbd
#endif
pigcs2NoDevSup_DBD += PI_GCS2Support.dbd

# Add all the support libraries needed by this IOC
pigcs2NoDevSup_LIBS += PI_GCS2Support
pigcs2NoDevSup_LIBS += motor
#ifdef ASYN
pigcs2NoDevSup_LIBS += asyn
#endif
#ifdef SNCSEQ
pigcs2NoDevSup_LIBS += seq pv
#endif

# pigcs2NoDevSup_registerRecordDeviceDriver.cpp derives from pigcs2NoDevSup.dbd
pigcs2NoDevSup_SRCS += pigcs2NoDevSup_registerRecordDeviceDriver.cpp

# Build the main IOC entry point on workstation OSs.
pigcs2NoDevSup_SRCS_DEFAULT += pigcs2NoDevSupMain.cpp
pigcs2NoDevSup_SRCS_vxWorks += -nil-

# Add support from base/src/vxWorks if needed
#pigcs2NoDevSup_OBJS_vxWorks += $(EPICS_BASE_BIN)/vxComLibrary

# Finally link to the EPICS Base libraries
pigcs2NoDevSup_LIBS += $(EPICS_BASE_IOC_LIBS)

#===========================

include $(TOP)/configure/RULES
#----------------------------------------
#  ADD RULES AFTER THIS LINE

