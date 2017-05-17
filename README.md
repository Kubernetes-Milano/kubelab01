# Kubelab01++, getting started
Qui si travano i file di configurazione per mettere in piedi un 
ambiente virtuale locale al proprio computer.

Questi file sono utilizzati nella sesssione pratica ***Kubelab01++*** organizzata
tramite la piattaforma *meetup.com*.

Il riferimento URL è [kubelab](https://www.meetup.com/kubernetes-milano/events/239987565). 

# HowTo
## Requisiti
In questa sessione come strumento per fare provisioning è utilizzato **Vagrant**. 
Per scaricare lo strumento [click here](https://www.vagrantup.com/downloads.html).

Il provider utilizzato è **Virtualbox**. Per scaricare [click here](https://www.virtualbox.org/wiki/Downloads).


## Guida

Per la maggior parte delle versioni linux è sufficiente un comando 

```bash
vagrant up
```

dalla riga di comando. Tuttavia in alcuni casi, per esempio Fedora, 
è richiesto un esplicito  riferimento al provider per la creazione 
di macchine virtuali. In quest'ultimo caso eseguire il comando 

```bash 
vagrant up --provider virtualbox 
``` 

Il comando farà partire una macchina virtuale con sistema operativo `coreos` il cui hostname è `kubelab`.

## Login ssh

Per collegarsi in ssh a *kubelab* eseguire il camando 

```bash
vagrant ssh
```

# Perché Vagrant
Lo srumento Vagrant permette di velocizzare il deploy della macchina virtuale. 
Infatti, fornsce uno stratto di astrazione aggiuntivo e rende flessibile la costruzione/ricostruzione 
di ambienti virtuali per attività di laboratorio/test.

## Da dove si parte?

Il `Vagrantfile` estrae i parametri di configurazione esposti come variabili  in `config.rb`. 
Questo permette di parametrizzare la convergenza dello stato del cluster. Inoltre, permette di gestire 
programmaticamente quante risorse assegnare a ogni VM in parte, per esempio: 
- CPU; 
- RAM;
- Networking. 

## Alternative

Per il deploy del run time Linux CoreOS, Vagrant non l'unica modalità. Ogni specifico contesto 
permette una modalità ad hoc. Per ogni ulteriore dettaglio informativo riferire la documentazione 
sul sito di CoreOS. L'URL di partena è [CoreOS deploy](https://coreos.com/os/docs/latest).




# Deploy di Kubernetes
## Topologia infrastrutturale del cluster 

Nel nostro caso specifico, il cluster è formato da un singolo nodo. 
Il sistema operativo CoreOS è configurato tramite il file di configurazione `cloud-config` contenuto in `user-data`. 
L'effetto del file di configurazione è la seguente:
- Avviare il demone Docker; 
- Creare un utente dedicato `kubelab:kubelab`.



```text
N.B. 

La notazione kubelab:kubelab è una notazione che si usa molto spesso in 
ambito Linux. Essa rappresenta "NomeUtente":"GruppoACuiNomeUtenteAppartiene"
```

# Credits

[CoreOS Vagrant](https://coreos.com/os/docs/latest/booting-on-vagrant.html)
