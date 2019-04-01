# CESI_Apache

Module Apache - CESI

## Formations

Web Concepteurs
Développeurs Informatiques




## Installation d'une machine virtuelle Debian 9 sur VirtualBox


### Configuration réseau sur VirtualBox

#### Réseau Invité ‹-› Système Hôte

Mode d'accès réseau : Accès privé hôte

Cela permet de créer un nouveau réseau entre les machines virtuelles et le système hôte. Le système hôte et les machines virtuelles ont accès à leurs ressources communes, mais pas au reste du réseau auquel le système hôte est connecté ni à internet.

Dans ce mode, votre machine virtuelle ne peut communiquer qu'avec votre machine hôte. Pour cela, une carte Ethernet virtuelle est spécifiquement créée sur la machine hôte (vboxnet0). Cette carte se configure de la même manière qu'une carte physique standard (ifconfig vboxnet0...). Cela permet de pouvoir travailler en réseau avec une machine virtuelle alors qu'aucune carte physique n'est présente (dans l'avion ou au milieu du désert par exemple).

Pour information :
➩ Adresse réseau : 192.168.56.0
➩ DHCP : actif

Pour accéder au premier système invité depuis le système hôte :
➩ http://192.168.56.101/

Pour accéder au système hôte depuis un des systèmes invités :
➩ http://192.168.56.1/

#### Réseau Invité ‹-› Réseau Hôte / Internet

Mode d'accès réseau : Accès par pont

Ce mode crée un pont vers la carte réseau du système hôte. Dans le réseau local, la machine virtuelle est visible, elle est vue exactement comme n'importe quel autre ordinateur de ce réseau. Elle a donc accès à toutes les ressources réseau (y compris internet) que les autres ordinateur du réseau local.

Pour information :
➩ DHCP : actif si celui-ci est actif sur le réseau local

#### Réseau Invité ‹-› Réseau Invité

Mode d'accès réseau : Réseau interne

Cela permet de créer un nouveau réseau entre les machines virtuelles. Elles n'accèdent pas au réseau local des machines physiques. Il n'y à donc pas d'accès à internet et pas d'accès aux ressources du réseau local.

Ce mode permet de connecter des machine virtuelle entre-elles sur un réseau virtuel isolé de la machine hôte. Par défaut le premier réseau virtuel est nommé « intnet ».

Pour information :
➩ Adresse réseau : non configuré
➩ DHCP : inactif

#### Réseau Invité -› Système Hôte / Internet

Mode d'accès réseau : NAT

Fait de la transposition d'adresse avec le système hôte. La machine virtuelle utilise la connexion réseau du système hôte pour communiquer avec internet. La machine virtuelle est invisible dans le réseau local et n'a accès à aucun ordinateur sauf celui du système hôte.

Dans ce mode, les trames sortant de votre machine virtuelle posséderont la même adresse que votre machine hôte (quelle que soit l'adresse IP de votre machine virtuelle). Une translation d'adresse réseau est systématiquement effectuée (Network Adresse Translation). Particularité : Dans ce mode, la machine virtuelle ne peut être utilisée qu'en client (navigation, mail, etc.) et non en serveur. Elle ne peut pas recevoir de requêtes directes de l'extérieur.

Pour information :
➩ Adresse réseau : 10.0.2.0
➩ Passerelle : 10.0.2.2
➩ DHCP : actif

Pour accéder au système hôte depuis un des systèmes invités :
➩ http://10.0.2.2/
