ARO Network Node — Headless VPS Setup Guide (Testnet S2)
Complete, battle-tested guide to running an ARO Server node on a Linux VPS — including the Serial Number extraction trick for servers without public inbound IPs.

🎁 Bonus: registering via dashboard.aro.network/signup?referral=C8RS grants a +20% daily mining boost for 14 days.

Why ARO, why now
Fact	Detail
Stage	Testnet Sprint 2 (live) — TGE announced for Q4 2026
Rewards	100M Jade points/day distributed to node operators; Jade converts to $ARO at mainnet
Funding	$2.1M raised
Cost to run	$0 if you already have a VPS / phone / PC
Quickstart (Ubuntu/Debian)
sudo su -
apt update && apt install -y wget curl
wget -O /tmp/aro-client-1.0.0.deb https://download.aro.network/files/deb/aro-client-1.0.0.deb
apt install -y -f /tmp/aro-client-1.0.0.deb
Expect: ARO installed successfully.

Getting the Serial Number on a headless/NAT'd server
The node's web console listens on localhost:40001 but many VPS providers don't route inbound IPv4. Workaround — a temporary Cloudflare quick tunnel (free, no account):

wget -q https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb -O /tmp/cf.deb
apt install -y /tmp/cf.deb
cloudflared tunnel --url http://localhost:40001
Open the printed *.trycloudflare.com URL in a browser → the console shows your Serial Number. Close the tunnel afterwards (Ctrl+C).

Bind the node
Dashboard → ARO Nodes → Add New Node → Server → paste SN → name it → confirm detected location → Add. Node should show Online 🟢.

"Cannot find your device" right after install = the agent hasn't finished registering with ARO's backend yet. Wait 5–10 min and retry.

Post-install checklist
[ ] Link an EVM wallet in your ARO profile (tokens are paid to it at TGE — seed phrase on paper, offline)
[ ] Disable OS sleep to protect uptime: systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
[ ] Check Campaigns tab for free Badges / bonus Jade missions
[ ] Points are distributed daily — day-one zero is normal
[ ] Residential IP devices (phone/home PC via the mobile & desktop apps) stack with your server node
Official links
Site: https://aro.network
Dashboard: https://dashboard.aro.network
Docs: https://docs.aro.network
Guide written from a real installation, Sept 2026. Referral disclosure: signing up via the link above gives you a 14-day +20% boost and pays the author a small commission from ARO's side — your rewards are unaffected.
