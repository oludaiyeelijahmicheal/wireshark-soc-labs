# Wireshark SOC Labs

Week 1 extra project, Networkwalks internship. I played a SOC analyst investigating network captures in Wireshark.

## Skills practiced
| Area | What I did |
|---|---|
| Follow TCP Stream | Rebuilt conversations as readable text, including a plain-text chat and web pages |
| Hidden data | Found content inside HTML comments that browsers do not display |
| Plain-text credentials | Located usernames and passwords sent over HTTP and FTP |
| Brute-force detection | Spotted repeated failed FTP logins and who sent them |
| VoIP analysis | Found SIP call setup, counted RTP voice packets, replayed a call |
| Statistics tools | Used Protocol Hierarchy, Conversations and Expert Information |

## Display filters I used
- `tcp && !(tcp.port == 80 || tcp.port == 443)`
- `http.content_type contains "text/html"`
- `http.request.method == "POST"`
- `ftp.response.code == 530`
- `tcp.analysis.retransmission`
- `ip.addr == <host>`

## Lessons learned
- **Filter first, then click.** A good display filter turns thousands of packets into a handful.
- **Plain text is readable by anyone.** HTTP, FTP, unencrypted chat and VoIP expose passwords, messages and calls. HTTPS, SFTP and SRTP fix that.
- **Hidden does not mean secret.** A comment inside a page is invisible to users but visible in the packets.

## Ethical use
All work was done inside the lab environment. Never capture traffic on a network you do not own or have written permission to test.

Related: [Lab setup (VirtualBox + Kali)](https://github.com/oludaiyeelijahmicheal/cybersecurity-lab-setup) · [Packet capture tasks](https://github.com/oludaiyeelijahmicheal/wireshark-packet-capture)
