# Interesting-Things
Single-WebApp-Target essentials scanning methodology tool starting at recon-information gathering for the juicy stuff ended up in exploitation.<br><br>

Let's suppose and you are browsing your gathered main host subdomains or you are in the process of the exploitation for specific target and faced a host that you need to :


```
- Fuzz it's main directory without getting a lot of flase positives during content-discovery process.
- Fuzz it's subdomains , looking for nice hidden services or administrator dashboards.
- Gather it's URLS from more than one resource and spidering the host looking for different functionalities , content managments systems or just more params.
- Filter - Grep - Sed those URLS results into common vulnerabilities effecting extract params and get/save gathered JS files to make the next steps more clear.
- Scan it's ports with services detections plus find out public CVE's related to those services and output the results to grepable text files , xml and nice looking HTML template.
- Running blind new common application CVE's detection scripts , common security misconfigurations , sub-takeover scanning and more.
- Setting time limit in secconds for each work process to be clear with your piority into the targeted host and avoiding taking too much time on gathering process for specific hosts.
```

Instead of doing all of this by running a single command line for each process and move you make , you can do it all on one command to make it much easier to understand host different functionalities and navigate to manual testing or process the output files as input for another exploitation tools.



<br>
<br>

### Workflow

<p align="center">
  <img  src="https://i.imgur.com/ha1IJJ6.png">
</p>


### Install - Configurations - Usage


Make sure you have these tools installed and works globally.

[FFUF](https://github.com/ffuf/ffuf),
[nuclei](https://github.com/projectdiscovery/nuclei),
[timelimit](https://zoomadmin.com/HowToInstall/UbuntuPackage/timelimit),
[Hakrawler](https://github.com/hakluke/hakrawler),
[GAU](https://github.com/lc/gau),
[Gospider](https://github.com/jaeles-project/gospider),
[xurls](https://github.com/mvdan/xurls),
[gf](https://github.com/tomnomnom/gf),
[NMAP](https://github.com/nmap/nmap),
[gf-patterns](https://github.com/1ndianl33t/Gf-Patterns)


- Configurations

```bash
Edit the file.
Example: 
# Word lists - Change - 
http_FFUF_wordlist="/lists/quickhits-2000.txt"; # fuzzing main directory 
https_FFUF_wordlist="/lists/quickhits-2000.txt"; #fuzzing main directory 
ffuf_sub_list="/SecLists/Discovery/DNS/medium-words.txt";


# nuclei_template - Change - 
nuclei_template="/oneline/nuclei-templates/";
zilePATH="/tools/zile/zile.py"; # Set zile tool path


# Control tool running time.  - Change - ( in secconds )
# Every mentioned tool will take a 60 seconds to gather URLs according to this configurations

gau_timelimit="60"; 
hakrawler_timelimit="60";
gospider_timelimit="60";



# Telegram Bot

telegram_bot_access_token="xx"; # Change to your telegram bot access token.
telegram_group_id="xx"; # Change to your telegram group id without -

```
<br>

- Usage

```bash

git clone https://github.com/osamahamad/Interesting-Things
cd Interesting-Things
chmod +x interest
./interest sub.target.com
OR
./interest target.com

```

```
If you want to use globally :
mv interest /usr/bin/interest
```

```
# I recomend to add this line in the last line of you tool if you are working on VPS ( if you want to copy the files to your public_html direcotry to browse the results using the browser. 
message Result%3A%20http%3A%2F%2FVPS_IP%2Finteresting-targets%2F$1$(date | jq -sRr @uri) ;
cp -r $1  /var/www/html/host/public_html/interesting-targets/$1

```


### Output 

Directory named [ interesting-targets ] -> targetname -> 
```
http-ffuf-filename.out
https-ffuf-filename.out
fuf_subdomains.out
target.out

/scrap/all-js-urls.out
/scrap/all-urls.out
/scrap/gau.out
/scrap/gospider.out
/scrap/hakrawler.out
/scrap/patterns/*.out
/scrap/zile.out

/NMAP/nmap-bootstrap.xsl
/NMAP/nmap-scan-result.gnmap
/NMAP/nmap-scan-result.nmap
/NMAP/nmap-scan-result.xml
/NMAP/nmap-scan-result.html

/nuclei/*.out
```

### Credits

All these tools creators : 

[FFUF](https://github.com/ffuf/ffuf),
[nuclei](https://github.com/projectdiscovery/nuclei),
[timelimit](https://zoomadmin.com/HowToInstall/UbuntuPackage/timelimit),
[Hakrawler](https://github.com/hakluke/hakrawler),
[GAU](https://github.com/lc/gau),
[Gospider](https://github.com/jaeles-project/gospider),
[xurls](https://github.com/mvdan/xurls),
[gf](https://github.com/tomnomnom/gf),
[NMAP](https://github.com/nmap/nmap),
[gf-patterns](https://github.com/1ndianl33t/Gf-Patterns)

@phspade for the function of telegram bot messages , I like it more than slack actually ( didn't know about it before ) and convert mostly all my tools from slack notification to telegram.

InfoSec Community.
