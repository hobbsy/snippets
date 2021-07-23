## How to allow youtube-dl to update without sudo

When attempting to update youtube-dl on a laptop running Ubuntu 20.04.2 LTS using the command:

`` youtube-dl -U ``

I get an error:

`` ERROR: no write permissions on /usr/local/bin/youtube-dl ``

This is fixed if you re-run that command as sudo:

`` sudo youtube-dl -U ``

However - if you would prefer to do this without superuser powers, you can change the user owner of the script from root to your own username with this command:

`` sudo chown $USER:$USER /usr/local/bin/youtube-dl ``

and then 

`` youtube-dl -U `` 

should work for you without errors

found via Wilf's answer on:
https://askubuntu.com/a/633141

