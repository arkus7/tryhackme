# Day 5: Ho-Ho-Hosint 

Elf Lola is an elf-of-interest. Has she been helping the Christmas Monster? lets use all available data to find more information about her! We must protect _The Best Festival Company!_

Resources available [here](https://blog.tryhackme.com/ho-ho/).

---

**Before**

Install `exiftool`

```sh
sudo apt install exiftool
```

Use `exiftool` to read metadata of the asset file

```sh
exiftool ./assets/thegrinch.jpg
```

Output:
```
ExifTool Version Number         : 11.99
File Name                       : thegrinch.jpg
Directory                       : .
File Size                       : 69 kB
File Modification Date/Time     : 2020:06:18 18:57:23+02:00
File Access Date/Time           : 2020:06:18 18:57:23+02:00
File Inode Change Date/Time     : 2020:06:18 18:57:32+02:00
File Permissions                : rw-r--r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.01
Resolution Unit                 : None
X Resolution                    : 1
Y Resolution                    : 1
XMP Toolkit                     : Image::ExifTool 10.10
Creator                         : JLolax1
Image Width                     : 642
Image Height                    : 429
Encoding Process                : Progressive DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 642x429
Megapixels                      : 0.275
```

## 1. What is Lola's date of birth? Format: Month Date, Year(e.g November 12, 2019)

We can see an username that Lola uses in the metadata of the image file: `JLolax1`

Open Google and search for `JLolax1` - you can find Twitter account of Elf Lola.

Answer:
```
December 29, 1900
```

## 2. What is Lola's current occupation?

```
Santa's Helpers
```

## 3. What phone does Lola make?

```
iPhone X
```

## 4. What date did Lola first start her photography? Format: dd/mm/yyyy

Use `WayBackMachine` to fin what's the date of first appearance of the Lola's WordPress blog.

The first date is 23/10/2019. But when you open the webiste at this year, you can see a text saying:

>Five year celebration!
>
>I started as a freelance photographer five years ago today! To celebrate, I am knocking 20% of all event photography days! 

Answer:
```
23/10/2014
```

## 5. What famous woman does Lola have on her web page?

Download image from Lola's blog. Use reverse search of Google Images.

Answer:
```
Ada Lovelace
```