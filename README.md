# The-Invisible-Internet-Project-I2P-

<img width="1024" height="1024" alt="IMG_1995" src="https://github.com/user-attachments/assets/41be827e-2bb2-463c-9ca9-44f931402fcc" />



The Invisible Internet Project (I2P)
A technical guide for I2P (the Invisible Internet Project): what it is, how it works, how to communicate and host services on it, installation and access instructions, operational security tips, benefits, and risks. See the docs/ directory for expanded topic files.[i2p +1]
Quick summary
I2P is a fully encrypted, peer-to-peer anonymous overlay network designed for hosting internal services (eepsites), secure peer-to-peer apps, email, chat, and anonymous file sharing within its own ecosystem. It is a different design from Tor: I2P focuses on internal services and garlic routing, while Tor focuses on anonymized access to the clearnet via onion routing and exit nodes.[i2p +1]
Table of contents
•	What is I2P?
•	How it works (short)
•	Installation (Linux, macOS, Windows)
•	Initial configuration and router console
•	Browser and client configuration
•	Five practical things to do
•	OPSEC and security recommendations
•	Benefits and risks
•	Further reading and references
What is I2P?
I2P is an anonymous overlay network that provides end-to-end encrypted tunnels between peers, a distributed network database (netDb), and an internal service ecosystem (eepsites, mail, IRC, BitTorrent). I2P nodes run a local router and communicate using unidirectional tunnels and garlic routing to increase resistance to traffic analysis.[i2p +1]
How it works (short)
When started, the I2P router reseeds, builds exploratory tunnels, and populates the netDb with RouterInfo records from peers. Communications use separate inbound and outbound tunnels and bundling of messages (garlic routing). The router exposes a local web-based console at http://127.0.0.1:7657 for monitoring and configuration.[i2p +1]
Installation
Important: Use the official downloads for your platform and prefer the Java reference implementation for compatibility and support. Official docs and bundles are the source for these steps.[i2p +1]
Linux (Debian/Ubuntu)
1.	Install Java 17+ (OpenJDK):  
sudo apt update && sudo apt install openjdk-17-jre-headless
2.	Download the I2P Debian package from the official site or add the I2P apt repository per the installation guide.
3.	Install package:  
sudo dpkg -i i2p*.deb  
sudo apt -f install  # fix deps if needed
4.	Start the router service:  
sudo systemctl enable –now i2p
5.	Open the router console at http://127.0.0.1:7657 to finish setup.[i2p +1]
macOS
1.	Install Java 17+ (via Homebrew or Azul Temurin).
2.	Use the macOS Easy Install bundle (official) when available for simpler setup, or download the generic installer and run the included I2P launcher.
3.	Launch I2P and open http://127.0.0.1:7657 to proceed with the setup wizard.[i2p]
Windows
1.	Download the Easy Install Bundle (bundled Java + I2P) from the official site.
2.	Run the installer; it will create a pre-configured Firefox profile (optional) and install the I2P service.
3.	Launch I2P and open http://127.0.0.1:7657 for the router console and initial configuration.[i2p]
Notes
•	The Easy Install Bundle is recommended for new users because it includes Java and a pre-configured browser profile. Expect bootstrapping time on first run. Allow the router to run for best performance.[i2p]
Initial configuration & router console
1.	Open http://127.0.0.1:7657 after starting I2P. The setup wizard will guide language, bandwidth share, and reseeding. Expect the router to take 3–10 minutes to become usable and several hours–days for optimal performance.[i2p]
2.	Configure bandwidth: increase the default conservative limits to improve throughput and network health via http://127.0.0.1:7657/config.[i2p]
3.	Check tunnels, peers, and netDb from the console; keep the router running continuously to avoid performance penalties caused by repeated reseeding and low reliability.[i2p]
Browser and client configuration
Browser (recommended: Firefox)
•	Configure a dedicated profile (about:profiles) or use the Easy Install Bundle’s pre-configured profile.
•	In Firefox Settings → Network Settings → Manual proxy configuration: set HTTP proxy 127.0.0.1 port 4444. This routes .i2p traffic through the I2P HTTP proxy.[i2p]
•	about:config tweaks: set media.peerConnection.ice.proxy_only = true (prevent WebRTC leaks); keyword.enabled = false; browser.fixup.domainsuffixwhitelist.i2p = true. Always prefix .i2p addresses with http://.[i2p]
System-wide browsers (Chrome/Edge/Safari)
•	Chrome/Edge use OS proxy settings (affects all apps). Set the HTTP proxy to 127.0.0.1:4444 in system settings if you accept system-wide proxying. Safari uses macOS proxy settings similarly.[i2p]
I2P client ports and defaults
•	Router console: http://127.0.0.1:7657[i2p]
•	HTTP proxy: 127.0.0.1:4444 (configure browser)[i2p]
•	IRC tunnel proxy: 127.0.0.1:6668 (point an IRC client)[i2p]
•	Internal web server (Jetty) docroot: ~/.i2p/eepsite/docroot (Linux)[i2p]
Five practical things to do once connected
1.	Browse eepsites (.i2p) using the proxied browser. Use stats.i2p and tracker lists to discover sites.[i2p]
2.	Use I2PSnark (http://127.0.0.1:7657/i2psnark/) to torrent inside I2P. It’s isolated from clearnet torrents.[i2p]
3.	Register and use an I2P mail account with SusiMail (http://127.0.0.1:7657/susimail/) for encrypted internal email.[i2p]
4.	Join Irc2P via the local IRC proxy (127.0.0.1:6668) to chat on I2P IRC networks.[i2p]
5.	Host an eepsite by placing files in the docroot and registering a friendly name via address book services (stats.i2p or no.i2p).[i2p]
OPSEC and security recommendations
•	Never mix I2P and clearnet browsing in the same browser profile. Use a dedicated profile or the Easy Install Bundle’s isolated profile.[i2p]
•	Prevent WebRTC and other leak vectors via browser config (media.peerConnection.ice.proxy_only=true) and avoid browser extensions that break isolation.[i2p]
•	Keep I2P router uptime high; frequent restarts reduce reliability and performance. Increase shared bandwidth responsibly to help the net.[i2p]
•	Understand that anonymity is a system property — combine I2P with good operational security (no identifying uploads, careful metadata handling, separate identities).[i2p]
Benefits
•	Internal anonymity for services and P2P apps, strong resistance to simple censorship.[i2p]
•	Built-in application suite (I2PSnark, SusiMail, IRC, eepsite hosting) operating entirely inside the overlay.[i2p]
Risks and negative uses
•	Like any anonymous network, I2P can be misused; criminal marketplaces and illegal content exist on darknet overlays.[arstechnica +1]
•	Performance: I2P requires warm-up time and continuous uptime; latency and throughput are worse than clearnet and often different from Tor.[i2p]
•	OPSEC mistakes (mixed profiles, browser leaks, revealing metadata) are the most common causes of deanonymization.[i2p]
I2P vs Tor (short)
•	Tor: onion routing, bidirectional circuits, exit nodes for clearnet access — optimized for anonymized browsing of the public internet.[i2p]
•	I2P: garlic routing, unidirectional tunnels, internal-focused services (eepsites) — optimized for hosting and communicating inside an overlay network.[i2p +1]
Files in this repo
•	README.md (this file)
•	docs/what-is-it.md
•	docs/how-it-works.md
•	docs/communication.md
•	docs/install-access.md
•	docs/benefits.md
•	docs/negative-use.md
•	docs/when-to-use.md
•	docs/i2p-vs-tor.md
•	.gitignore
References
All operational details and installation guidance are drawn from the official I2P documentation and getting started guide.
