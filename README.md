# Kubelab01++, getting started instructions

Questa repository vi aiutera' a creare un nodo `coreos` che utilizzeremo durante il prossimo `kubelab`. 

# HowTo

L'unico comando da lanciare e' `vagrant up`. Il comando fara' partire una macchina virtuale `coreos`, per collegarsi in ssh alla macchina lanciare `vagrant ssh`.

# Come funziona

Il `Vagrantfile` estrae i parametri settati in `config.rb` per capire in che stato portare il cluster e quante risorse assegnare ad ogni macchina (CPU/RAM/Networking). Nel nostro caso specifico, il cluster e' costituito da un singolo nodo. Una volta creata la macchina, viene applicato il `cloud-config` contenuto in `user-data` che si assicurera' di avviare il demone docker e creera' un utente dedicato `kubelab:kubelab`.

# Credits

[CoreOS Vagrant](https://coreos.com/os/docs/latest/booting-on-vagrant.html)
