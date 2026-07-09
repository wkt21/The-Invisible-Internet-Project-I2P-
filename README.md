# The-Invisible-Internet-Project-I2P-

<img width="1024" height="1024" alt="IMG_1995" src="https://github.com/user-attachments/assets/41be827e-2bb2-463c-9ca9-44f931402fcc" />

# The Invisible Internet Project (I2P)

A technical guide for I2P (the Invisible Internet Project): what it is, how it works, how to communicate and host services on it, installation and access instructions, operational security tips, benefits, and risks. See the `docs/` directory for expanded topic files. [web:12][web:16]

## Quick summary

I2P is a fully encrypted, peer-to-peer anonymous overlay network designed for hosting internal services, secure peer-to-peer applications, email, chat, and anonymous file sharing within its own ecosystem. It is different from Tor: I2P focuses on internal services and garlic routing, while Tor focuses on anonymized access to the clearnet via onion routing and exit nodes. [web:12][web:13]

## Table of contents

- What is I2P?
- How it works
- Installation
- Initial configuration and router console
- Browser and client configuration
- What you can do with it
- OPSEC and security recommendations
- Benefits and risks
- I2P vs Tor
- References

## What is I2P?

I2P is an anonymous overlay network that provides end-to-end encrypted tunnels between peers, a distributed network database, and an internal service ecosystem including eepsites, mail, IRC, and BitTorrent. I2P nodes run a local router and communicate using unidirectional tunnels and garlic routing to increase resistance to traffic analysis. [web:12][web:13]

## How it works

When started, the I2P router reseeds, builds exploratory tunnels, and populates the network database with peer records. Communications use separate inbound and outbound tunnels and bundling of messages through garlic routing. The router exposes a local web-based console at `http://127.0.0.1:7657` for monitoring and configuration. [web:13][web:16]

## Installation

Use the official downloads for your platform and prefer the Java reference implementation for compatibility and support. The steps below are based on the official I2P documentation and getting started guide. [web:12][web:16]

### Linux (Debian/Ubuntu)

1. Install Java 17+:
   ```bash
   sudo apt update && sudo apt install openjdk-17-jre-headless

Download the I2P Debian package from the official site or add the official I2P apt repository.

Install the package:
sudo dpkg -i i2p*.deb
sudo apt -f install

Start and enable the router service:
sudo systemctl enable --now i2p

Open the router console at  http://127.0.0.1:7657  to finish setup. [web:12][web:16]

macOS
1.	Install Java 17+ using Homebrew or Azul Temurin.
2.	Use the official macOS Easy Install Bundle when available, or download the generic installer and run the included I2P launcher.
3.	Launch I2P and open  http://127.0.0.1:7657  to proceed with the setup wizard. [web:16]
Windows
1.	Download the Easy Install Bundle from the official site.
2.	Run the installer, which can create a pre-configured Firefox profile and install the I2P service.
3.	Launch I2P and open  http://127.0.0.1:7657  for the router console and initial configuration. [web:16]
Initial configuration and router console
1.	Open  http://127.0.0.1:7657  after starting I2P. The setup wizard will guide language, bandwidth share, and reseeding. Expect the router to take several minutes before it becomes usable, and longer before it reaches peak performance. [web:16]
2.	Configure bandwidth to improve throughput and network health by visiting  http://127.0.0.1:7657/config . [web:16]
3.	Check tunnels, peers, and network database status from the console, and keep the router running continuously to avoid repeated reseeding and low reliability. [web:16]
Browser and client configuration
Firefox recommended

<img width="1170" height="741" alt="IMG_1997" src="https://github.com/user-attachments/assets/e0b82ae9-e6bd-4feb-992e-ed726ec6d555" />


media.peerConnection.ice.proxy_only = true
keyword.enabled = false
browser.fixup.domainsuffixwhitelist.i2p = true

Always type  http://  before  .i2p  addresses. [web:16]






Chrome, Edge, and Safari
Chrome and Edge use system-wide proxy settings, which affect all applications on your system. On Windows, configure the OS proxy settings to use  127.0.0.1:4444 . On macOS, Safari uses the system proxy settings in the same way. [web:16]
Common I2P ports
•	Router console:  http://127.0.0.1:7657 
•	HTTP proxy:  127.0.0.1:4444 
•	IRC tunnel proxy:  127.0.0.1:6668 
•	I2PTunnel manager:  http://127.0.0.1:7657/i2ptunnel/ 
•	I2PSnark:  http://127.0.0.1:7657/i2psnark/ 
•	SusiMail:  http://127.0.0.1:7657/susimail/ 
•	Address book:  http://127.0.0.1:7657/dns  [web:16]
What you can do with it
Browse  .i2p  websites
The most immediate use of I2P is browsing hidden websites through your proxied browser. I2P also supports address book services for discovering and registering sites. [web:16]
Use I2PSnark
I2PSnark is the built-in BitTorrent client for sharing and downloading torrents inside I2P. It operates entirely within the I2P network and does not connect to clearnet torrents. [web:16]
Send email with SusiMail
SusiMail is a web-based email client designed to reduce identifying leaks and support email use inside the I2P network. [web:16]
Chat on IRC
I2P includes a pre-configured IRC tunnel so you can connect an IRC client to the I2P IRC network through the local proxy. [web:16]
Host your own site
You can publish an eepsite by placing HTML files in the I2P site docroot and then registering a human-readable name through an address book service. [web:16]
OPSEC and security recommendations
•	Never browse I2P and the clearnet in the same browser profile.
•	Use a dedicated Firefox profile or the Easy Install Bundle’s isolated profile.
•	Prevent WebRTC and other leak vectors through browser configuration.
•	Keep the I2P router running continuously.
•	Treat anonymity as a system property and keep identities separated.
•	Avoid exposing metadata through uploads, file names, or reused accounts. [web:16][web:13]
Benefits and risks
Benefits
•	Internal anonymity for services and peer-to-peer apps.
•	Resistance to simple censorship.
•	Built-in applications for torrents, email, chat, and eepsite hosting. [web:12][web:16]
Risks and negative uses
•	I2P can be misused, including by criminal marketplaces or illegal content distributors.
•	Performance is slower than the clearnet and requires warm-up time.
•	Operational mistakes such as profile mixing or browser leaks can compromise anonymity. [web:6][web:7][web:16]
I2P vs Tor
•	Tor primarily anonymizes access to the public internet and uses exit nodes.
•	I2P is optimized for internal services and self-contained anonymous communication.
•	Tor uses onion routing.
•	I2P uses garlic routing and unidirectional tunnels. [web:12][web:13][web:16]
References
•	Official I2P documentation: Docs
•	Official getting started guide: Getting started with I2P
