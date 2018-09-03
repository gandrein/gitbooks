# DD-WRT on TP-LINK Archer C9 v2

## How to install DD-WRT (01.08.2018)

On 01.08.2018, all of the July and August DD-WRT builds bricked the router when attempting to flash the `factory-to-ddwrt` binary.

After going through the DD-WRT forum, [a user reported](https://forum.dd-wrt.com/phpBB2/viewtopic.php?p=1139729#1139729) version `12292017-r34311` was successful. So I tried it and indeed I managed to flash the factory image.

### Installation Steps

I have downloaded `12292017-r34311` from this betas listing: 
https://download1.dd-wrt.com/dd-wrtv2/downloads/betas/
* select a 2017 and then 29-12-2017-r34311
* search for archer-c9v2 and descend into that folder
* copy the two bin files locally

For instructions, follow this great video https://www.youtube.com/watch?v=naWXf-d33Pk

I have used the both the `factory-to-ddwrt` and the `archer-c9v2-webflash.bin` for that version. At the date of this writing, I have not updated to a newer DD-WRT build. May consider to do so in the future.


### Bricked Router

When bricked I have followed the exact steps described in this great video https://www.youtube.com/watch?v=AU8RyW82Z2M  

At that time, I have used Windows for this, exactly as in the video since I did not have the patience of figuring out how to properly set-up `tftpd` transfer on Linux. 


### Extra Resources

The official DD-WRT Wiki for Archer C9 is this https://wiki.dd-wrt.com/wiki/index.php/TP_Link_Archer_C9. It has references to this more comprehensive [FAQ list](https://wiki.dd-wrt.com/wiki/index.php/Index:FAQ#Where_do_I_download_firmware.3F).

The links to DD-WRT beta builds can be found on the FAQ list:_Where do I download firmware?_ 