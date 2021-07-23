## How to allow youtube-dl to update without sudo

When attempting to update youtube-dl on a laptop running Ubuntu 20.04.2 LTS using the command:

`` youtube-dl -U ``

I get an error:

`` ERROR: no write permissions on /usr/local/bin/youtube-dl ``

This is fixed if you re-run that command as sudo:

`` sudo youtube-dl -U ``

However - if you would prefer to do this without superuser powers, you can change the user owner of the script from root to your own username 

Firstly you might want to show that root:root is in charge?

`` ls -la  /usr/local/bin/youtube-dl ``

Then run this command:

`` sudo chown $USER:$USER /usr/local/bin/youtube-dl ``

re-running this:

`` ls -la  /usr/local/bin/youtube-dl ``

you should now see that your username:username is the owner of the youtube-dl script rather than root

and then simply retry running your initial command:

`` youtube-dl -U `` 

It should now work without the write permissions error.


found via Wilf's answer on:
https://askubuntu.com/a/633141

