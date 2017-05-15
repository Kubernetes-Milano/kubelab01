# Installazione del sistema operativo CoreOS

A seguire si descriverà l'insieme di attività da compiere 
per installare manualmente un sistema operativo CoreOS. 

Supponiamo di aver lanciato il Sistema in modalità di sola lettura. Per poter installare il SO è necessario creare il 
file *file-config*. Questo file è il manifesto di configurazione del sistema. 

## Creazione della password di accesso e il file *cloud-config* 

Eseguire il seguente comando

```bash
openssl passwd -1 > cloud-config
```

Questo comando chiederà di inserire due volte una string a 
scelta che diventerà la password di login. 

```text 
N.B. Controllare che la scheda di rete sia correttamente configurata per andare in rete. 
```

Completare il file cloud-config con 


```yaml
#cloud-config

hostname: core01.ovirt.iks.local
users: 
  - name: "kubelab"
    passwd: "$1$T.SZZGry$jrXJfzyMzy3rIYUfJhNXV/"
    groups:
       - sudo
       - docker

```

```text 
N.B. Il valore della chiave passwd è una stringa codificata con il comando precedente openssl.
```

A questo punto è possibile installare CoreOS, il container native operating system.


## Installazione di CoreOS

Assumendo che la rete sia opportunamente configurata procediamo con l'installazione di CoreOS.


Invocare il comando dalla directory ~/ */home/core* 

```sh
sudo coreos-install -d /dev/sda -C stable -c cloud-config
```

L'opzione "-d" specifica la location dove installare l'OS. È usuale, nel caso di un unico disco, che 
il sistema operativo faccia montare il disco nella location "/dev/sda". 

L'opzione "-C" specifica la versione dell'immagine ISO da installare. Le possibilità sono
- Alfa;
- Beta;
- Stable.

Infine, con "-c" si indica il file minifest per la configurazione del sistema operativo. 
Da notare che ogni configurazione tramite cloud-config è da preferire alla classica maniera tramite
modifiche manuali.

## Riavviare CoreOS

Appena il sistema ha terminato di fare le proprie attività procedere con il riavvio del sistema. Ricordarsi 
di togliere il DVD ISO di installazione dal lettore ottico. 

```sh
reboot 
```







