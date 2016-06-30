QQ_MAC couldn't login after using lantern maybe

try kill process network,use:
#!/bin/bash

pid=$( ps -ef | grep "/usr/libexec/networkd$" | awk '{print $2}' )
sudo kill -9 $pid
