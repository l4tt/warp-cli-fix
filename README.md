# Cloudflare warp no internet connection after disconnect fix

<p>I have been using cloudflare's warp for about a year now and just stumbled onto this issue when i switched to linux, *cough* Ubuntu 20.4
the issue presents it's self as when i disconnect from the warp itself i am left with no WIFI connection at all.</p>

##  Issue 
<p> There ctl tool is great accept for one thing, it changes /etc/resolv.conf to cloudflares nameservers when you connect to a warp. but when you disconnect it doesn't go back to the org it just leaves the cloudflare nameservers. </p>

##  Fix 
<p> Some people say just regenerate the service file with resolvconf but how do you install that with no wifi?? you rlly can't and therefor you would have to reconnect to the warp. but at that point you probs already uninstalled cloudflares shitty warp off your box. so what do you do?. </p>

<b> Well this is how you fix the problem</b>
```bash
sudo rm /etc/resolv.conf # Removes the config file, After this please open a diffren't console window!
ifconfig # Please copy the DNS that starts with 192.x.x.x
sudo nano /etc/resolv.conf # Reopen the file and type the following lines

### Config Issue Fix
nameserver 8.8.8.8
nameserver 192.x.x.x # The DNS you copyied goes here

```
<p> that's it now save, and relaunch you're browser and it should be fixed. 
Today we learned that even tho it might hide you for a little it still is pain to fix if issues occure </p>
