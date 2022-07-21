# SunTime
Simple sunset and sunrise time calculation python library.

## Installation

Using pip:

    pip3 install suntime
    
Or download and type:

    python3 setup.py install

## Usage

You can use the library to get UTC sunrise and sunset times typing:

```python3
import time
from suntime import Sun, SunTimeException

latitude = 51.21
longitude = 21.01

sun = Sun(latitude, longitude)

# Get today's sunrise and sunset in UTC
today_sr = sun.get_sunrise_time()
today_ss = sun.get_sunset_time()
print('Today at Warsaw the sun raised at {}:{} and get down at {}:{} UTC'.
      format(today_sr[3], today_sr[4], today_ss[3], today_ss[4]))

# On a special date
abd = (2014, 10, 3, 10, 0, 0, 0, 0, -1)
abd_sr = sun.get_sunrise_time(abd)
abd_ss = sun.get_sunset_time(abd)
print('On {}-{}-{} the sun at Warsaw raised at {}:{} and got down at {}:{}.'.
      format(abd[0], abd[1], abd[2], abd_sr[3], abd_sr[4], abd_ss[3], abd_ss[4]))

# Error handling (no sunset or sunrise on given location)
latitude = 87.55
longitude = 0.1
sun = Sun(latitude, longitude)
try:
    abd_sr = sun.get_sunrise_time(abd)
    abd_ss = sun.get_sunset_time(abd)
    print('On {}-{}-{} at somewhere in the north the sun raised at {}:{} and got down at {}:{}.'.
          format(abd[0], abd[1], abd[2], abd_sr[3], abd_sr[4], abd_ss[3], abd_ss[4]))
except SunTimeException as e:
    print("Error: {0}.".format(e))
```

## License

Copyright © 2019 SatAgro Sp. z o.o. and contributors:

* Krzysztof Stopa ([kstopa](https://github.com/kstopa))
* Andrey Kobyshev ([yokotoka](https://github.com/yokotoka))
* Matthias ([palto42](https://github.com/plato42))
* Hadrien Bertrand ([hbertrand](https://github.com/hbertrand))


This file is part of SunTime library for python (SunTime).

SunTime is free software: you can redistribute it and/or modify it under the terms of the GNU Lesser General Public License as published by the Free Software Foundation, either version 3 of the License, or any later version.

SunTime is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU Lesser General Public License for more details.

You should have received a copy of the GNU Lesser General Public License along with CAMS tools. If not, see http://www.gnu.org/licenses/.
