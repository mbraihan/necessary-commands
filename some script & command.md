alias dfc="df -h /dev/sda1 --output=source,fstype,size,used,avail,pcent"

du -h -s *

du -sm Pictures/* | sort -nr
