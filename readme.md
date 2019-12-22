# TON Contest

Manual DNS resolver
0. Change directory to manual_dns
1. Compile code.fc (including stdlib.fc and shared/dns.fc):
   func -PSR -ocode.fif stdlib.fc ../shared/dns.fc code.fc
2. Run Fift-script: fift -s <script>.fif
   Next scripts available:
     - mdns-new.fif - create ext_msg to create new smart contract
     - mdns-add.fif - create ext_msg to add dns record (pair <domain name, array [category, address]>)
     - mdns-owner.fif - create ext_msg to change owner of smart contract
3. Also next get-methods available: dnsresolve and seqno

Automatic DNS resolver
0. Change directory to automatic_dns
1. Compile code.fc (including stdlib.fc and shared/dns.fc):
   func -PSR -ocode.fif stdlib.fc ../shared/dns.fc code.fc
2. Run Fift-script: fift -s <script>.fif
   Next scripts available:
     - adns-new.fif - create ext_msg to create new smart contract
     - adns-add.fif - create req to some wallet to add dns record (pair <domain name, array [category, address]>)
3. Also next get-methods available: dnsresolve and expire_at
