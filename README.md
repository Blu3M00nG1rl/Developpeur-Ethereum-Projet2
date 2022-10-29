# Developpeur-Ethereum-Projet2
Projet 2 de la formation développeur ethereum
Test d'un smart contract de voting

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
5 describe pour 31 tests au total:
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

  Contract: Voting
    test addVoter/getVoter
      ✓ should not add voter if not owner (573ms)
      ✓ should not add voter if voters registration is not open (148ms, 95032 gas)
      ✓ should not add voter if voter is already registered (19ms)
      ✓ should have voter registered (74ms, 50220 gas)
      ✓ should not get voter data if not voter (24ms)
      ✓ should get voter data (18ms)
    test addProposal/getProposal
      ✓ should not submit proposal if not voter (32ms)
      ✓ should not submit proposal if it is not allowed (65ms, 30599 gas)
      ✓ should not submit blank proposal (22ms)
      ✓ should have proposal registered (69ms, 59268 gas)
      ✓ should not get proposal data if not voter (11ms)
      ✓ should store proposal in array, get proposal (55ms, 59268 gas)
    test setVote
      ✓ should not get voter data if not voter (13ms)
      ✓ should not voting if session havent started yet (12ms)
      ✓ should not voting if have already voted (76ms, 88655 gas)
      ✓ should have not found the proposal (34ms, 30554 gas)
      ✓ should get vote id (95ms, 108567 gas)
      ✓ should have voted (67ms, 108567 gas)
    test states : event, revert
      ✓ should start proposal registering, get event WorkflowStatusChange (37ms, 95032 gas)
      ✓ should end proposal registering, get event WorkflowStatusChange (177ms, 125631 gas)
      ✓ should start voting session, get event WorkflowStatusChange (101ms, 156185 gas)
      ✓ should end voting session, get event WorkflowStatusChange (118ms, 186718 gas)
      ✓ should not start or end proposals and voting if not owner, revert (42ms)
      ✓ should not start proposals registering, revert (202ms, 125631 gas)
      ✓ should not end proposals registering, revert (11ms)
      ✓ should not start voting session, revert (11ms)
      ✓ should not end voting session, revert (12ms)
    test tallyVotes
      ✓ should not tally votes if not owner, revert (12ms)
      ✓ should not tally votes if voting session is not ended, revert (11ms)
      ✓ should tally votes, get event WorkflowStatusChange (81ms, 94098 gas)
      ✓ should display the winning proposal description (68ms, 94098 gas)

·------------------------------------------|----------------------------|-------------|----------------------------·
|   Solc version: 0.8.17+commit.8df45f5f   ·  Optimizer enabled: false  ·  Runs: 200  ·  Block limit: 6718946 gas  │
···········································|····························|·············|·····························
|  Methods                                                                                                         │
·············|·····························|··············|·············|·············|··············|··············
|  Contract  ·  Method                     ·  Min         ·  Max        ·  Avg        ·  # calls     ·  eur (avg)  │
·············|·····························|··············|·············|·············|··············|··············
|  Voting    ·  addProposal                ·           -  ·          -  ·      59268  ·          24  ·          -  │
·············|·····························|··············|·············|·············|··············|··············
|  Voting    ·  addVoter                   ·           -  ·          -  ·      50220  ·          76  ·          -  │
·············|·····························|··············|·············|·············|··············|··············
|  Voting    ·  endProposalsRegistering    ·           -  ·          -  ·      30599  ·          20  ·          -  │
·············|·····························|··············|·············|·············|··············|··············
|  Voting    ·  endVotingSession           ·           -  ·          -  ·      30533  ·           4  ·          -  │
·············|·····························|··············|·············|·············|··············|··············
|  Voting    ·  setVote                    ·       58101  ·      78013  ·      70892  ·          20  ·          -  │
·············|·····························|··············|·············|·············|··············|··············
|  Voting    ·  startProposalsRegistering  ·           -  ·          -  ·      95032  ·          27  ·          -  │
·············|·····························|··············|·············|·············|··············|··············
|  Voting    ·  startVotingSession         ·           -  ·          -  ·      30554  ·          12  ·          -  │
·············|·····························|··············|·············|·············|··············|··············
|  Voting    ·  tallyVotes                 ·           -  ·          -  ·      63565  ·           3  ·          -  │
·············|·····························|··············|·············|·············|··············|··············
|  Deployments                             ·                                          ·  % of limit  ·             │
···········································|··············|·············|·············|··············|··············
|  Voting                                  ·           -  ·          -  ·    2077414  ·      30.9 %  ·          -  │
·------------------------------------------|--------------|-------------|-------------|--------------|-------------·

  31 passing (35s)
