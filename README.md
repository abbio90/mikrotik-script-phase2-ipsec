# mikrotik-script-phase2-ipsec

Quante volte avete instaurato un tunnel peer to peer ipsec e dai log vedete solo lo stato della fase1?

Ho realizzato questo articolo MIKROTIK SCRIPT STATO IPSEC, in maniera che fosse possibile scrivere nei log lo stato della fase 2 di un peer ipsec.


Questo può venir integrato con invio notifica telegram, invio mail, suono buzzer del router, accensione user-led e in un'infinità di modi.

Ora non rimane che commentare il peer ipsec che vogliamo monitorare.

Come fare?

Vai nel terminale e digita /ip ipsec print

/ip ipsec peer print Flags: X - disabled; D - dynamic; R - responder 
0 ;;; Peer-Edok
name="peer-edok" address=1.10.10.11/32 profile=profile_edok exchange-mode=main send-initial-contact=yes
1 D name="l2tp-out-GREENET-" address=1.11.11.12/32 local-address=192.168.100.2 profile=default exchange-mode=main send-initial-contact=yes
2 D name="gre-tunnel5" address=1.12.12.13/32 profile=default exchange-mode=main send-initial-contact=yes
3 D name="gre-tunnel4" address=1.13.13.14/32 profile=default exchange-mode=main send-initial-contact=yes
4 D name="gre-tunnel2" address=1.14.14.15/32 profile=default exchange-mode=main send-initial-contact=yes
5 D name="gre-tunnel3" address=1.15.15.16/32 profile=default exchange-mode=main send-initial-contact=yes

Come potrete notare affianco a ogni ipsec a prescindere che sia statico o dinamico è presente in numero di riferimento.

Nel mio caso, il peer ipsec da commentare sarà il numero 0.

Andiamo nel terminale e aggiungiamo il commento al peer ipsec rappresentato dal numero 0 nel print precedente.

/ip ipsec peer set comment= numbers=0 Peer-Edok



In questa maniera abbiamo inserito il commento, per verificarne l'effettiva modifica possiamo digitare nel terminale il comando: /ip ipsec peer export show sensitive.
