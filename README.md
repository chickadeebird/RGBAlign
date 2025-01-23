# RGBAlign

This is a Pixinsight script for determining the relative shift of RGB channels within an image using the peaks of the smaller stars within the image. The script will then realign the channels either in a specified corner or globally across the image. For the global realignment, the script calculates the misalignment in 16 different regions across the image and realigns the channels for each region.

This script is meant to address the issues of imperfect demosaicing and chromatic aberration due to RGB misalignment.

# Usage

The star detector tab permits adjustment of the Pixinsight Star Detector. Testing of the star detector is made possible with this tab. It is not necessary to capture all of the stars, as only the 50 smallest stars detected are used as a general measure of the RGB alignment.

RGB Align Full Image works by partiioning the image into 16 regions. The divisions along the image edges are from 0-10%, 10-50%, 50-90%, and 90-100% of both the image width and the height, thus creating 16 subregions of unequal sizes. The smaller regions are in the corners, and the outside edges are the next smallest region, with the middle regions being the largest. This method of partitioning was done to optimize the realignment of the RGB channels due to chromatic aberration, which may be most prominent in the corners and the edges. If there is a global RGB misalignment, the Align FUll Image algorithm also addresses this issue. Some denoising prior to alignment helps with the detection of small stars.

RGB Align Corner aligns a specified corner by selecting the corner and the percentage of the image defining the corner.

The sliders may be used to adjust the amount of correction on the realignment as needed.

## Uses

The script works on RGB images where the channels are misaligned and therefore displaying with unusual asymmetric halos around the stars.

## Images

This is a sample pair of an RGB image that is misaligned (left), and its realiged image after the script (right).

<img src="./figs/RGBAlign realigned stars.png" text='Deblurred stars using the "Stars Only" script - left blurry stars, right deblurred' align=left />

## Script

This is the script interface for the RGBAlign script.

<img src="./figs/RGBAlign script.png" text='RGBAlign script' align=left />

This can be found here: ChickadeeScripts > RGBAlign after installation.

## Manage repository location

In order to automatically install and subsequently refresh script updates in Pixinsight, add the following URL to Resources > Updates > Manage repositories

https://raw.githubusercontent.com/chickadeebird/RGBAlign/main/

After this has been added to the repositories, Resources > Updates > Check for updates should place the new RGBAlign script in Scripts > ChickadeeScripts


