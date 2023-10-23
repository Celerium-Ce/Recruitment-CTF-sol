# Height Of Joeys Plane
Helped me learn how to track flights just from a single image. Kinda crazy to see what all I could do with a single image
## Category
**OSINT**
## Points
**299**
## Challange Description
Mr. Joey Miller this, miller there, miller where. He wants to find the height of his plane after a year. Help him find the lat and long(in decimal upto 4 decimal), speed(mph) and height(feet) of the plane a year and 24 secs after this photo was taken.
## Attached file
![Picture](https://github.com/Celerium-Ce/Recruitment-CTF-sol/blob/main/Misc/Imgs/catch%20me%20if%20you%20can.jpg)
## Explanation
Since the statement asks for 1 year 24 seconds after the picture was taken. We first view the exif data of the image file to see when the image was taken

![Picture](https://github.com/Celerium-Ce/Recruitment-CTF-sol/blob/main/Misc/Imgs/Exif%20data%20haha.png)

Here we can see that the image was taken on `6:55:36 3 september 2022`. Now 1 year 24 seconds after that would be `6:50:00 3 september 2023`

Now to track the flight i used [FlightAware](https://www.flightaware.com/). The flight can be found using `VT-IFP` 

![FlightPage](https://github.com/Celerium-Ce/Recruitment-CTF-sol/blob/main/Misc/Imgs/Flight%20aware%20flight%20page.png)

From here we open the tracker logs of the flight and find the log at `6:56:00`

![FlightInfo](https://github.com/Celerium-Ce/Recruitment-CTF-sol/blob/main/Misc/Imgs/Flight%20Info.png)

Here we can see that `latitude=19.4032`	`Longitude=77.8842` `Height=33,000ft` `Speed=531mph`

## Flag
`d4rk{19.4032_77.8842_531_33000}`
