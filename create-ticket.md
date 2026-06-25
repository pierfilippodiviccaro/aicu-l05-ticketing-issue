# Issue: Create ticket with validation

## Request

```txt
Serve creare ticket dal supporto.
```

## Fatti (Facts)

- L'app è un'applicazione Express + React/Vite per la gestione di ticket di supporto (contesto noto dal corso AICU L03/L04).
- La richiesta non specifica campi obbligatori, validazione, né chi può creare il ticket.

## Assunzioni (Assumptions)

- [compila con ipotesi operative dichiarate]
- Il ticket ha almeno due campi: title (titolo) e description (descrizione).

## Domande Aperte (Questions)

- Il campo title ha una lunghezza minima? Se sì, quanti caratteri? (Da decidere in L06 prima di autorizzare la patch.)

## Decisione (Decision)

Per questo slice, "creare ticket" significa:

```txt
Un utente può inviare un form con title e description non vuoti;
il ticket viene salvato e compare in lista senza ricaricare la pagina.
```

## Fuori Scope / Non-Obiettivi (Non-Goals)

- Autenticazione o ownership del ticket (chi lo ha creato).
- Allegati, notifiche, priorità o stato del ticket.
- Validazione avanzata lato backend (lunghezza massima, sanitizzazione).

## Criteri Di Accettazione (Acceptance Criteria)

1. Il form accetta title e description e li invia al backend.
2. Se uno dei due campi è vuoto, il form non viene inviato e appare un messaggio di errore visibile.
3. Dopo l'invio con successo, il nuovo ticket compare in lista senza ricaricare la pagina.

## Piano Di Verifica Manuale (Manual Test Plan)

- Verifica 1: Compilare title e description e cliccare "Invia" → il ticket appare in lista e i campi del form si svuotano.
- Verifica 2: Lasciare title vuoto e cliccare "Invia" → il form non viene inviato e appare un messaggio di errore sul campo mancante.

## Note Per L06

- Quale payload esatto aspetta il backend (title, description, altri campi?).
- Come gestire errori di rete (timeout, 500) — mostrare messaggio o ignorare?
- Lunghezza minima/massima di title: da decidere prima di scrivere la validazione.
