#################################################
#                 HUE AUTO OFF                  #
#                                               #
#             version 1.2.0, 05/2023            #
#                                               #
#################################################

# 05/2023 v. 1.2.0
# Added ability to turn lights back on when reconnecting

# ----------------------------------------------------------------------------------

# Bash script for automatically turning off the lights when all predifined 
# IP-addresses have left WiFi on ASUSWRT Merlin

# Prerequisites: jq, curl, bash, jffs userscripts enabled
# To find out how to get your Hue API hash see https://developers.meethue.com/
# For this to work you mast have static DHCP enabled for the IP addresses you want to use
# To install, replace the variables under # User variables #, 
# Make sure you don't use a randomised MAC address on your device when connecting
# to your WiFi network.
#
# INSTALLATION: 
# Make script executable (chmod +x ./hueoff) and run "hueoff install" from CLI
# OR:
# Place this script in /jffs/scripts/
# create this folder: /jffs/scripts//hueoff.d/logs
# add the following lines  to /jffs/scripts/post-mount:
# /jffs/scripts/hueoff &> /jffs/scripts/hueoff.d/logs/log.txt &

# To see the log run "cat /jffs/scripts/hueoff.d/logs/log.txt"

########################################################################################

# Hue control functions were adapted from Harald van der Laan's Philips Hue
# Bash script: https://github.com/hvanderlaan/philips-hue
# ---------------------------------------------------------------------------------------
# kallefornia 2023
# https://github.com/duckwilliam/hueautooff