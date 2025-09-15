# bidrag-kafka
![](https://github.com/navikt/bidrag-kafka/workflows/setup%20kafka%20streams/badge.svg)

Hendelser for applikasjoner under team bidrag

### Les og skriv fra/til kafka topic fra terminalen
Dette forutsetter at [kcat](https://github.com/edenhill/kcat) og [nais-cli](https://doc.nais.io/cli/install/) er installert på maskinen

Følg denne [guiden](https://doc.nais.io/cli/commands/aiven/) for å koble deg til kafka-topic via nais-cli. 

Det er satt opp egen kafka-ACL for å koble deg til bidrag-journalpost-topic fra maksinen som heter `bidrag-cli` og `bidrag-cli-feature`.

Kjør følgende kommandoer:
```bash
nais aiven create kafka bidrag-cli-feature bidrag -s bidrag-kafka-cli-feature
## Hent path fra følgende kommando
nais aiven get kafka bidrag-kafka-cli-feature bidrag
## Og deretter kjør følgende kommando med path fra forrige kommando
export KCAT_CONFIG=<path>/kcat.conf

## Da skal du kunne lese siste meldinger fra kafka-topic
kcat -F $KCAT_CONFIG -t bidrag.journalpost-feature -C
```