# 😷 Dissecting Embedded Devices

## UART

### UART Identification Test

* Locate the headers or pads you believe could be UART by inspecting the board. (Seeing two to four pads/pins grouped together on the board is a good sign, but as mentioned earlier, they can be intermingled within other functional pads/pins.)
* Discover the target voltage by probing the board with a multimeter or identifying an IC and looking up the datasheet.
* Discover a ground that is easy to connect to by measuring resistance (Ohms) between a known ground (such as the chassis ground) and pins that are easy to connect to (effectively 0 Ohms between the known ground and the pin in question).
* Connect the board to your JTAGulator if you are fortunate enough to find headers, or solder a header to the board and then connect
* Verify the version of JTAGulator firmware . The version can be checked against the code on the repository at [https://github.com/grandideastudio/jtagulator/releases](https://github.com/grandideastudio/jtagulator/releases). If the version is not the latest, follow the directions at [www.youtube.com/watch?v=xlXwy-weG1M](https://www.youtube.com/watch?v=xlXwy-weG1M).
* Enable UART mode and set the target voltage
* Run the UART identification test
* On success, look for reasonable responses such as carriage returns or line feeds (0D or 0A).
* Verify the identified settings by running in pass-thru mode with the baud rate candidate (57600 in our case).

#### Commands

```
# Display Target Interfaces
> h

# Verify the version of JTAGulator firmware
> i

# Enable UART mode
> u

# Set the target voltage
> v

# Run the UART identification test
> u

# On success, look for reasonable responses such as carriage returns or line feeds (0D or 0A)

# Verify the identified settings by running in pass-thru mode with baud rate candidate (57600 in our case)
> p 
> 57600
```

## REFERENCES

* [https://github.com/grandideastudio/jtagulator/releases](https://github.com/grandideastudio/jtagulator/releases)
* &#x20;[www.youtube.com/watch?v=xlXwy-weG1M](https://www.youtube.com/watch?v=xlXwy-weG1M)

