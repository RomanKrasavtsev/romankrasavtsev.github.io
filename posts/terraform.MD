terraform state rm $(terraform state list | grep avi_ | awk 'ORS=" "')
