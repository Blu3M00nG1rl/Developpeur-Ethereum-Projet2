# Developpeur-Ethereum-Projet2
Projet 2 de la formation développeur ethereum
* Test d'un smart contract de voting

## Installation de l'environnement
1 - Lancement de ganache
2 - truffle init (pour créer l'environnement truffle : contracts, migrations, test, truffle-config.js)
3 - Création d'un fichier .env pour y intégrer des variables d'environnement (API KEY de INFURA et MNEMONIC de Ganache)
3 - truffle-config.js et .env : modification des paramètres de networks pour travailler en local ou sur un testnet (avec un clé infura ou alchemy)
4 - Alimentation du ichier script dans le dossier "migrations" pour l'import et le déploiement du smart contract
5 - Téléchargement des librairies dotenv, hdwallet-provider et openzeppelin (test-helpers et contracts)
6 - Téléchargement de eth-gas-reporter et intégration dans truffle-config.js : mocha (rapport sur la quantité de gas utilisé)

## Création du fichier de test
Le tests ont été répartis en plusieurs étapes :
* 5 describe pour 31 tests au total:

1. 'test addVoter/getVoter'
        6 tests : 1 expect, 4 expectRevert, 1 expectEvent
2. 'test addProposal/getProposal'
        6 tests : 1 expect, 4 expectRevert, 1 expectEvent
3. 'test setVote'
        6 tests : 1 expect, 4 expectRevert, 1 expectEvent
4. 'test states : event, revert'
        9 tests : 4 expectEvent, 5 expectRevert
5. 'test tallyVotes'
        4 tests : 1 expect, 2 expectRevert, 1 expectEvent

## Lancement du test et résultat eth-gas-reporter

* 31 passing (35s)

* eth-gas-reporter : 2077414 gas (30,9 % of 6718946 limit)