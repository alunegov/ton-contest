# TON Contest, Stage 1

## Task

Build one or more **smart contracts** for the TON network, suggest **improvements for FunC / TON VM**, or find **issues** and suggest **fixes** for the TON Testnet. See [TON Contest.txt](TON Contest.txt) for details.

## dev

SMC compilation, fift-script interpretation and BOC-file uploading to blockchain are performed with [TON](https://github.com/ton-blockchain/ton).

Tests can be executed with ```fift -s test_run.fif```.

## Manual DNS resolver

0. Change directory to **manual_dns**
1. Compile **code.fc** (including **stdlib.fc** and **shared/dns.fc**): ```func -PSR -ocode.fif stdlib.fc ../shared/dns.fc code.fc```
2. Run Fift-script: ```fift -s <script>.fif```. Next scripts available:
     - **mdns-new.fif** - create ext_msg to create new smart contract
     - **mdns-add.fif** - create ext_msg to add dns record (pair <domain name, array [category, address]>)
     - **mdns-owner.fif** - create ext_msg to change owner of smart contract
3. Also next get-methods available: **dnsresolve** and **seqno**

## Automatic DNS resolver (not completed)

0. Change directory to **automatic_dns**
1. Compile **code.fc** (including **stdlib.fc** and **shared/dns.fc**): ```func -PSR -ocode.fif stdlib.fc ../shared/dns.fc code.fc```
2. Run Fift-script: ```fift -s <script>.fif```. Next scripts available:
     - **adns-new.fif** - create ext_msg to create new smart contract
     - **adns-add.fif** - create req to some wallet to add dns record (pair <domain name, array [category, address]>)
3. Also next get-methods available: **dnsresolve** and **expire_at**

## Result

**III Place**

Issues from judges:

```
Manual DNS:
+ Almost good baseline implementation.
- There is no way to change previously added domains.
- There is no way to completely delete expired domains.

Automatic DNS:
+ Ability to receive donations.
+ Ability to withdraw earnings.
- seqno is not incremented in recv_external, so it is useless.
- No sanity checks for domain names, so anyone can completely block adding new domains to prefix dictionary.
- Updating and extending domain is not charged.
- No garbage collection for expired domains.
- It is not possible to replace non-owned expired domain.
- There is no way to customize domain fees.
- There is no way to customize domain expiration time.
- Owner check doesn't compare workchain_id.
```
