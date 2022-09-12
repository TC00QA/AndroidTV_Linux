# What am I?

I am a guide to installing linux on any cheap android TV box

## Table of contents
* Where to source a box
* What to look out for
  * Processors used
    * Amlogic S905*
    * Allwinner H6
    * Allwinner H616
    * Rockchip RK3318
    * Best performance
    * Additional notes
* What boxes can be used
* How to install linux (App)
* Flashing SD card
* Entering recovery mode
* How to install linux (SD)
* How to install linux (EMMC Flash)
* My experience
* No thrills install
* Notes

## Where to source a box

You can source most boxes through marketplace, amazon or ebay. Make sure you are buying from a trusted seller as some sellers may advertise more RAM than the processor can actually support.

## What to look out for

As previously mentioned look out for misleading advertisments, as a rule of thumb the 4 main processors are as follows

### Amlogic S905*

The amlogic S905x3 is the best processor to go for, be very carful when looking for listings of the S905. The normal S905 can handle a max of 2GB DDR2/DDR3 ram. This by far is the worst choice if you are looking for enough ram. Performace of the S905 is nothing to be snuffed at, however, for the same money you can buy the better S905x3. I would stick to the S905x3 for compatability. The S905x2 can be found but isnt as widely supported. The S905x3 is also perfect for machine learning as it has a built in NPU and NN Accelerator.

A priavte REPO is the only source to find modern builds

### Allwinner H6

The allwinner H6 is the older version of the H616. It sits somewhere performance wise inbetween the S905 and S905x3. This is a great chip if you can find it for cheaper. It supports up to 4GB of DDR3/DDR4 ram so should meet your needs. Additionally this silicon also has a slightly better GPU (Than the H616) if you need more graphical power.

Armlogic has native support as some SBC's are built on this, there are plenty of prebuilt images out there

### Allwinner H616

The H616 is a cheaper and more efficient version of the H6. It is a newer replacement and runs at a lower clockspeed to the H6 but performs the same. It also supports a higher resolution than the H6. I would reccomend the H6 over the H616 as the older model is better supported.

Armlogic has native support as some SBC's are built on this, there are plenty of prebuilt images out there

### Rockchip RK3318

If you are after raw GPU power this is definatley the chip to go for. With up to three times the GPU performance of the Amlogic S905x3 I would reccomend this if you're looking at running a GUI or will be doing GPU intensive tasks. What it makes up for in GPU horespower it lacks in CPU horsepower. Yet again pushing the S905x3 to my most reccomended.

Armlogic has native support as some SBC are built on this, there are plenty of prebuild images out there

### Best performance

-- Best CPU and NPU:        S905x3 \
-- Better CPU and OK GPU:     S905 \
-- Best GPU and OK CPU:     RK3318 \
-- Best efficieny and support:  H6 

### Additional notes

The amlogic processors arent officially supported by ARMBIAN, however there is someone who Is supporting them currently. You can either build your own kernel based on the most recent release or run a pre-complied image. Links are in the notes section

## What boxes can be used

Most boxes you find avaliable can be used, most of them are manufacturerd exactly the same. Your biggest factor at play will be the processor. It is down to you what processor you choose and why. Another main factor to be looking out for when purchasing is the name of the box. This will be something like X96 Max or T95. They may have different designs but the install guides are pretty much the same aslong as they have the same 'name'.

## How to install linux (App)

If you want to run linux without installing it to the TV or SD card you can run it in android. The app most commonly used is: Debian noroot (Link in notes)

## Flashing SD card

In my instance I installed armbian using a pre-complied image for the S905x3 (See linked in notes). You must flash the image provided to an SD card, balena etcher is my preffered goto but rufus may work aswell. Ignore any errors that may get thrown during verification becuase two partitions are made. Once you have done this you can move onto the next step. A simple google of "[PROCESSOR][TV_BOX_NAME]armbian" will throw up a tonne of results for images and guides

## Entering recovery mode

The easiest solution by far is the simplest one. On most (if not all) of these boxes there will be a 4 pole 3.5mm jack on the back labelled AV. If there is another jack on the back it might best best using a flashlight to identify what port contains a tac switch behind it (See notes) All you need to do with the box unplugged is hold down that switch. This is commonly done with a toothpick therfore is refferd to as 'the toothpick method'. While holding down the button simply plug the power back in. Once you see the first splashscreen (Typically the name of the box) stop pressing the button. You should then be able to see android recovery options.

Another method to enter recovery mode / install is to find an app called something along the lines of "Over the air update" or "System update". It will be an app somewhere in the app drawer. You can try searching for a "local" update file. There will be a button called local and it should automatically find the inserted SD card and there will typically be an option ending with .zip . You can simply click local, click the file ending with .zip and it should install arbiam for you. I havent had success doing it this way as typically you also need an unlocked bootloader and this is something that varies manufacturer to manufacturer. I reccomend the 'toothpick' method.

## How to install linux (SD)

Once you follow the guide to flash to your SD card you're done! There is nothing else you need to do, it is now running from the SD card. This means, however, everytime you need to get back into linux you will need to enter recovery mode.

##  How to install linux (EMMC Flash)

Assuming your unit has EMMC and not ROM (Typically EMMC) you can easily install arbian to your android tv box. All you need to do is run the command: $ armbian-install . From there, it is fairly straight forward. If using ophub's pre-complied installer (or another pre-complied image for allwinner / rockchip cpu) you will be presented with some options. You need to setup the date and time and locale. You will also be presented with a table. This table is so that the right DTB file will be used. This HAS to be the correct DTB file. In the table will be the processor type and the box name. Make sure both of these are the same as your purchased box otherwise you might brick your box. Type in the correct ID and the install will begin. 

The install can take between 10 - 30 mins, please, be patient. The box will install and work through everything at its own pace.

Once everything is installed, remove the TF / SD card and unplug / replug the power in. You should see a splash screen then linux should continue to load.

## My experience

I managed to install armbian linux with a pre-compiled image from OPHUB. As it uses the S905x3 the kernel dosent support it. Becuase of this you can either use a pre-complied arbian build or rebuild the kernel yourself with OPHUB's REPO. I managed to easily install linux and SSH into it via VSCode. I am running jenkins and docker. Using a 3 container docker build (One python, one MySQL and one NGINX) I am finding build times to be pleasantly surprising. It takes about 3 mins with the S905x3, compared to my desktop (i5 11300h) about 1 min. This performance is pleasantly suprising considering the S905x3 is rated 5W whereas the i5 is 30W. It is able to handle jenkins and this docker build easily with 4GB ram. In my testing also I only every hit about 50 degrees when building and deploying. This is surprising considering there is a relatively small metal heatsink on the APU. If you need some extra headroom It wouldnt be that hard to install a small laptop fan to help with cooling.

## No thrills install

Box I used: https://www.amazon.co.uk/Sleekview-Android-Cortex-Decode-USB3-0/dp/B094DB4TYR/ref=sr_1_1?crid=RXG40A02N633&keywords=h96+max&qid=1662988095&sprefix=h96+max%2Caps%2C87&sr=8-1
Time: GMT
Locale: London
DTB ID: 508

## Notes

I take NO credit for any content within the links, there are some links to other repos, the people who work to maintain these repos are amazing and I highly reccomened giving them a follow!

Debian noroot https://play.google.com/store/apps/details?id=com.cuntubuntu&hl=en_GB&gl=US

S905* Prebuilt images https://github.com/ophub/amlogic-s9xxx-armbian

Tac Switch https://www.google.com/search?q=tact+switch&source=lnms&tbm=isch&sa=X&ved=2ahUKEwjM2vCSno_6AhUVaMAKHcwrCeYQ_AUoAXoECAEQAw&biw=1920&bih=937&dpr=1&safe=active&ssui=on
