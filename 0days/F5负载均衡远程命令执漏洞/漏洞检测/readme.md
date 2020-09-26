CVE-2020-5902-Scanner
Automated script for F5 BIG-IP scanner (CVE-2020-5902) using hosts retrieved from Shodan API. You must have a Shodan account to use this script. Click here if you don't have Shodan account.

Installation
Install dependencies.
# CentOS & Fedora
sudo yum install git python3 -y

# Ubuntu & Debian
sudo apt install git python3 python3-pip -y
Clone repository & install python3 module
git clone https://github.com/aqhmal/CVE-2020-5902-Scanner.git
cd CVE-2020-5902-Scanner/
pip3 install -r requirements.txt
Add your Shodan API key
# Shodan API Key (change according to your Shodan API key)
api_key = ''
# Shodan search query
search_query = 'http.title:"BIG-IP&reg;- Redirect"'
Usage
python3 scanner.py
DISCLAIMER
This script is only for penetration testing and security research, I will not be responsible if you use it for illegal activities.
