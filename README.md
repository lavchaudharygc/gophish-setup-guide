# gophish-setup-guide
ull Gophish Installation &amp; Setup Guide (2025). Includes Golang install, Ngrok out-of-network HTTPS config, SMTP/Brevo setup, phishing templates, campaign launch steps, and troubleshooting. Designed for ethical hackers, red teams, and cybersecurity awareness training.

🛡️ Gophish Full Installation + Ngrok Out-of-Network Setup (Error-Free Guide — 2025 Update)
By: Lav Chaudhary (GCS ISLET | Garun Cyber Security)

This guide provides a complete, error-free tutorial on how to install Gophish, configure Golang, set up Ngrok tunneling, integrate an SMTP service (Brevo), and launch a fully working phishing campaign from outside the network.

Optimized with keywords:
Gophish installation, Gophish full setup 2025, Gophish Ngrok tutorial, phishing simulation tool, ethical hacking labs, red team tools, cybersecurity India, phishing campaign setup, Gophish templates.

📌 Prerequisites

Make sure you have:

Linux OS (Kali, Ubuntu or Debian-based)

Golang installed

Ngrok account (for HTTPS tunneling)

SMTP provider like Brevo, Gmail, or any SMTP server

Basic Linux terminal knowledge

1️⃣ Install Required Packages
sudo apt update && sudo apt upgrade -y
sudo apt install unzip wget -y

2️⃣ Install Golang (Required by Gophish)
wget https://go.dev/dl/go1.22.6.linux-amd64.tar.gz
sudo rm -rf /usr/local/go
sudo tar -C /usr/local -xzf go1.22.6.linux-amd64.tar.gz
echo "export PATH=$PATH:/usr/local/go/bin" >> ~/.bashrc
source ~/.bashrc
go version


Expected output:
go version go1.22.6 linux/amd64

3️⃣ Download & Setup Gophish
wget https://github.com/gophish/gophish/releases/download/v0.12.1/gophish-v0.12.1-linux-64bit.zip
unzip gophish-v0.12.1-linux-64bit.zip
cd gophish
chmod 755 gophish

4️⃣ Start Gophish Server
./gophish


Admin Panel URL: https://0.0.0.0:3333

Default Username: admin

Password: Shown in terminal during first run (auto-generated)

5️⃣ Ngrok Out-of-Network Setup (HTTP Port 80)
Add Ngrok Auth Token:
ngrok config add-authtoken YOUR_AUTH_TOKEN

Start Ngrok Tunnel:
ngrok http 80


You will get an HTTPS link like:

https://abcd1234.ngrok-free.app


➡️ Use this link as your phishing page landing URL.

6️⃣ Configure Gophish Admin Panel
🔑 Login

Open: https://0.0.0.0:3333

Enter default credentials → Change password.

📮 Sending Profile (SMTP Setup with Brevo)

Go to Sending Profiles → New Profile

Enter details:

Field	Value
Name	Brevo SMTP
From	"Your Name" <youremail@example.com>
Host	smtp-relay.brevo.com:587
Username	Your email
Password	Your API Key

Click Send Test Email → check your inbox.

🖥️ Landing Page Setup

Go to Landing Pages → New Page

Paste your phishing HTML template

Uncheck Capture Credentials (if not required)

Set Redirect URL to original legitimate website login page

📧 Create Email Template

Go to Email Templates → New Template

Add subject + email body

Enable tracking pixel if needed

🚀 Launch Campaign

Go to Campaigns → New Campaign

Enter:

Field	Value
Name	Instagram Demo / Test Campaign
Email Template	Choose template
Landing Page	Select your phishing page
Sending Profile	Brevo SMTP
URL	Your Ngrok HTTPS URL
Group	Add recipients (test emails first)

Click Launch Campaign

📊 Monitor Campaign Results

Dashboard will show:

Emails Delivered

Emails Opened

Link Clicked

Data Submitted (if enabled)

Browser & OS info
