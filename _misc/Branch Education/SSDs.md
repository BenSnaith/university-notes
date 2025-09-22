How does an SSD work?

![[Untitled.png]]

Inside of an SSD there are one or many NAND Flash Memory chips, and inside each of these chips contains a V-NAND

  

**V-NAND (Vertical NAND)**

  

Every picture, message and bit of information is saves as quantities of electrons inside memory cells of the V-NAND which are called charge trapped flash. These structures are insanely small and complex.

  

**Saving a picture to your smartphone**

  

Each picture is made up of pixels and each pixels has a colour, the colour of every pixel is defined by a combination of three numbers, ranging from 0 to 255, representing RGB. each of these numbers from 0-255 is represented by 8-bits or a byte. Therefore each pixel takes 24-bits or 3 bytes, these values are then stored like a big long list called an array.

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|10010110  <br>10101101  <br>11101111|10010110  <br>10101101  <br>11101111|10010110  <br>10101101  <br>11101111|10010110  <br>10101101  <br>11101111|10010110  <br>10101101  <br>11101111|10010110  <br>10101101  <br>11101111|
|10010110  <br>10101101  <br>11101111|10010110  <br>10101101  <br>11101111|10010110  <br>10101101  <br>11101111|10010110  <br>11111101  <br>11101111|10010110  <br>10101101  <br>11101111|10010110  <br>10101101  <br>11101111|
|10010110  <br>10101101  <br>11101111|10010110  <br>10101101  <br>11101111|10010110  <br>10011101  <br>11101111|10010110  <br>10101101  <br>11101111|10010110  <br>10101101  <br>11101111|10010110  <br>10101101  <br>11101111|
|10010110  <br>10101101  <br>11101111|10010110  <br>10101101  <br>11101111|10010110  <br>10101101  <br>11101111|10010110  <br>10101101  <br>11101111|11110110  <br>10101101  <br>11101111|10010110  <br>10101101  <br>11101111|
|10010110  <br>10101101  <br>11101111|10010110  <br>11101101  <br>11101111|10010110  <br>10101101  <br>11101111|10010110  <br>10101101  <br>11101111|10010110  <br>10101101  <br>11101111|10010110  <br>10101101  <br>11101111|
|10010110  <br>10101101  <br>11101111|10010110  <br>10101101  <br>11101111|10010110  <br>10101101  <br>11101111|10010110  <br>10101101  <br>11101111|10010110  <br>10001101  <br>11101111|10010110  <br>10101101  <br>11101110|

  

**The bigger picture**

  

Now, we’re gonna zoom out to see the bigger picture, which in out example is:  
4032 x 3024 = 12,192,768 or 12Megapixels  
12,192,768px * 24bit/pixel = 293,626,432-bits  

  

**Let’s open up the SSD**

  

Inside the SSD, there are V-Nand chips, and inside these chips there are millions of  
  
**Charge Trap Flash Memory Cells,** In each cell we can store information by placing different levels of electrons onto **Charge trap.** Most memory cells in modern day can hold 8 different levels of charge with some cutting edge technologies holding 16 levels of charge. This means that a single cell instead of using 1 cell for 1-bit (1, 0) now a single cell hold hold 3 bits of information (4-bits on cutting edge design). If we took a cell and had a very low charge on it, it would be stored as 111, whereas some charge would be 100, and a lot of electrons would be 000, there are 8 levels for the various amount of electron charges that are possible.

The key to the charge trap is that when it is charged it can hold onto this charge for decades, which is how information is saved or written to the SSD. In order the read the cell, the amount of charge is measured. In order to remove that data from a charge trap all of the electrons are forcibly removed from the charge trap forcing it to it’s lowest level, which is 111 leaving no excess behind.

  

**Verticality**

  

These Charge Trap Flash Cells are layered vertically up to 10 called a string. When information is written to or read from a string only one cell can be activated at any given time. to do this we use a separate control gate attached to every layer of this string/tower.

The bottom control gate first asks CT1 for its charge level.  
CT1 then sends this information up the string to the bitline (info highway) at the top.  
This is done all the way up to 10.  

The same sequence is done when adding to a charge cell. The main concept is **only one CT can be accessed at any given time.**

  

**Getting more complex**

  

Next, we duplicate this idea of a string (tower) 32x, which gets up a **page** of strings (going across by control gate) and the collection of pages is called a row (the entire amalgamation). we also have 32 Bitlines across the top. Every cell on one page shares the same control gate it stretches across all.

Next, we duplicate these rows x6 until we get a block.

![[Untitled 1.png]]

The top of each string shares a bitline going along the column, we have to add an addition control gate to control which row is gonna be used at a time, these are called bitline selectors, the bitlines are like highways and the selectors acts as traffic lights that mediate the information flow so only a single row can use the highway at a time. Similarly the control gate for each later CT[1-10] act as traffic lights for those layers, This means it can read from or write two any given page at any given time.

  

**The size**

  

The actual dimensions of these in unknown as is it a well kept secret but range from about 96-136 layers tall, this is still only 1/4 the height of a sheet of paper.

A page can be 30,000 - 60,000 memory cells wide.

Blocks are 4-8 rows and there are 4000, 6000 blocks.

Along the edges are the control gate selectors and bitline selectors and by using these we can access one page.

The information from this page (bit long row of CT) is fed to the bitline and then to the page buffer, opposite for writing