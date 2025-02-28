### Check Battery Status
```sh
#!/bin/bash

# Check if the system has a battery
battery_status=$(upower -i $(upower -e | grep battery) | grep -E 'state|percentage')

if [ -z "$battery_status" ]; then
    echo "No battery found."
else
    echo "$battery_status"
fi
```
### Copy this to ```/opt/tools/bat```
### Make above file executable and add to path variable
