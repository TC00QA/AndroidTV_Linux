# What am I?

I am a guide to installing linux on any cheap android TV box

## Table of contents
- Where to source a box
- What to look out for
 -- Processors used
  -- Amlogic S905*
  -- Allwinner H6
  -- Allwinner H616
  -- Rockchip RK3318
  -- Best performance
  -- Additional notes
- What boxes can be used
- Flashing SD card
- How to install linux (App)
- How to install linux (SD)
-  How to install linux (EMMC Flash)

## Where to source a box

You can source most boxes through marketplace, amazon or ebay. Make sure you are buying from a trusted seller as some sellers may advertise more RAM than the processor can actually support.

## What to look out for

As previously mentioned look out for misleading advertisments, as a rule of thumb the 4 main processors are as follows

### Amlogic S905*

The amlogic S905x3 is the best processor to go for, be very carful when looking for listings of the S905. The normal S905 can handle a max of 2GB DDR2/DDR3 ram. This by far is the worst choice if you are looking for enough ram. Performace of the S905 is nothing to be snuffed, however, for the same money you can buy the better S905x3. I would stick to the S905x3 for compatability. The S905x2 can be found but isnt as widely supported. The S905x3 is also perfect for machine learning as it has a built in NPU and NN Accelerator.


### Allwinner H6

The allwinner H6 is the older version of the H616. It sits somewhere performance wise inbetween the S905 and S905x3. This is a great chip if you can find it for cheaper. It supports up to 4GB of DDR3/DDR4 ram so should meet yours needs. Additionally this silicon also has a slightly better GPU if you need more graphical power.

### Allwinner H616

The H616 is a cheaper and more efficient version of the H6. It is a newer replacement and runs at a lower clockspeed to the H6 but performs the same. It also supports a higher resolution than the H6. I would reccomend the H6 over the H616 as the older model is better supported.

### Rockchip RK3318

If you are after raw GPU power this is definatley the chip to go for. With up to three times the GPU performance of the Amlogic S905x3 i would reccomend this if your are looking at running a GUI or will be doing GPU intensive tasks. What it makes up for in GPU horespower it lacks in CPU horepower. Yet again pushing the S905x3 to my most reccomended.

### Best performance

-- Best CPU and NPU:        S905x3 \
-- Better CPU and OK GPU:     S905 \
-- Best GPU and OK CPU:     RK3318 \
-- Best efficieny and support:  H6 \

### Additional notes

The amlogic processors arent officially supported by ARMBIAN, however there is someone who Is supporting them currently. You can either build your own kernel based on the most recent release or run a pre-complied image. Links are in the notes section

## What boxes can be used

Most boxes you find avaliable can be used, most of them are manufacturerd exactly the same. Your biggest factor at play will be the processor. It is down to you what processor you choose and why. Another main factor to be lookign out for when purchasing is the name of the box. This will be something like X96 Max or T95. They made have different designs but the install guides are pretty much the same aslong as they have the same 'name'.

## Flashing SD card

In my instance I install armbian using a pre-complied image for the S905x3 (See linked in notes). You must flash the image provided to an SD card, balena etcher is my preffered goto but rufus may work aswell. Ignore any errors that may get thrown during verification becuase two partitions are made. Once you have done this you can move onto the next step

## Entering recovery mode

The easiest solution by far it the simplest one. On most (if not all) of these boxes there will be a 4 pole 3.5mm jack on the back labelled AV. If there is another jack on the back it might best best using a flashlight to identify what port contains a tac switch behind it (See notes)

## How to install linux (App)

If you want to run linux without installing it to the TV or SD card you can run it in android. The app most commonly used is: Debian noroot (Link in notes)

## How to install linux (SD)

Once you follow the guide to flash to your SD card you're done! There is nothing else you need to do, it is now running from the SD card. This means, however, everytime you need to get back into linux you will need to enter recovery mode

##  How to install linux (EMMC Flash)

# Notes

I take NO credit for any content within the links, there are some links to other repos, the people who work to maintain these repos are amazing and I highly reccomened giving them a follow!

Debian noroot https://play.google.com/store/apps/details?id=com.cuntubuntu&hl=en_GB&gl=US

S905* Prebuilt images https://github.com/ophub/amlogic-s9xxx-armbian

Tac Switch https://www.google.com/search?q=tact+switch&source=lnms&tbm=isch&sa=X&ved=2ahUKEwjM2vCSno_6AhUVaMAKHcwrCeYQ_AUoAXoECAEQAw&biw=1920&bih=937&dpr=1&safe=active&ssui=on
