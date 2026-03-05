
# Introducció a Blockchain

---

## La pregunta

- Com podem mantenir un **registre digital compartit** entre múltiples participants?
- Sense confiar en:
  - un **servidor central**
  - una **autoritat única**
- Però assegurant:
  - integritat
  - coherència
  - resistència a manipulacions

---

## Sistemes centralitzats

<div style="width:70%; margin:auto;">

```mermaid
%%{init: {'themeVariables': {'fontSize': '24px'}}}%%
flowchart TD
    U1[Usuari] --> S[(Servidor central)]
    U2[Usuari] --> S
    U3[Usuari] --> S
    U4[Usuari] --> S
```

</div>

Problemes:

- punt únic de fallada
- censura
- manipulació possible
- dependència d'una autoritat

---

## Sistema descentralitzat

<div style="width:70%; margin:auto;">

```mermaid
%%{init: {'themeVariables': {'fontSize': '24px'}}}%%
flowchart TD
    A[Node] --- B[Node]
    B --- C[Node]
    C --- D[Node]
    D --- A
    A --- C
    B --- D
```

</div>

Característiques:

- cada node té una còpia del registre
- verificació distribuïda
- sense autoritat central

---

# Bitcoin

---

## Bitcoin

- Primera aplicació de **blockchain**
- Proposada el **2008**
- Autor: **Satoshi Nakamoto**

Objectiu:

> Sistema de **pagament electrònic peer-to-peer**

---

## Flux d'una transacció

<div style="width:75%; margin:auto;">

```mermaid
sequenceDiagram
    participant U as Usuari
    participant N as Nodes
    participant M as Miners
    participant B as Blockchain

    U->>N: Envia transacció
    N->>M: Propaga transacció
    M->>M: Validació
    M->>B: Inclou en bloc
```

</div>

---

## Bloc de Bitcoin

<div style="width:65%; margin:auto;">

```mermaid
%%{init: {'themeVariables': {'fontSize': '24px'}}}%%
flowchart LR
    H[Hash bloc anterior]
    T[Transaccions]
    TS[Timestamp]
    N[Nonce]
    H2[Hash del bloc]

    H --> H2
    T --> H2
    TS --> H2
    N --> H2
```

</div>

---

## Cadena de blocs

<div style="width:60%; margin:auto;">

```mermaid
%%{init: {'themeVariables': {'fontSize': '24px'}}}%%
flowchart LR
    B1[Bloc 1] --> B2[Bloc 2]
    B2 --> B3[Bloc 3]
    B3 --> B4[Bloc 4]
```

</div>

Propietat clau:

- si es modifica un bloc
- canvia el **hash**
- es trenca la cadena

➡️ **immutabilitat**

---

# Ethereum

---

## Ethereum

Blockchain programable.

Permet:

- **smart contracts**
- **dApps**
- **DeFi**
- **NFTs**

Creat per **Vitalik Buterin (2015)**

---

## Smart Contracts

<div style="width:60%; margin:auto;">

```mermaid
%%{init: {'themeVariables': {'fontSize': '24px'}}}%%
flowchart LR
    User[Usuari] --> SC[Smart Contract]
    SC --> Result[Resultat automàtic]
```

</div>

---

## Ethereum Virtual Machine

<div style="width:65%; margin:auto;">

```mermaid
%%{init: {'themeVariables': {'fontSize': '24px'}}}%%
flowchart TD
    User[Usuari]
    Node[Node Ethereum]
    EVM[EVM]
    Contract[Smart Contract]

    User --> Node
    Node --> EVM
    EVM --> Contract
```

</div>

---

# Estructura de dades

---

## Blockchain com a registre append-only

<div style="width:60%; margin:auto;">

```mermaid
%%{init: {'themeVariables': {'fontSize': '24px'}}}%%
flowchart LR
    D1[Dada 1] --> D2[Dada 2]
    D2 --> D3[Dada 3]
    D3 --> D4[Dada 4]
```

</div>

Propietats:

- només **afegir dades**
- no es poden modificar dades antigues

---

# Validació de transaccions

---

## Signatures digitals

<div style="width:60%; margin:auto;">

```mermaid
%%{init: {'themeVariables': {'fontSize': '24px'}}}%%
flowchart LR
    PK[Clau privada] --> SIG[Signatura]
    SIG --> TX[Transacció signada]
    TX --> NET[Xarxa blockchain]
```

</div>

---

## Validació en la xarxa

<div style="width:65%; margin:auto;">

```mermaid
%%{init: {'themeVariables': {'fontSize': '24px'}}}%%
flowchart TD
    TX[Transacció] --> V1[Validació signatura]
    V1 --> V2[Comprovació saldo]
    V2 --> V3[Regles protocol]
    V3 --> OK[Acceptada]
```

</div>

---

# Arquitectura d'una dApp

---

<div style="width:75%; margin:auto;">

```mermaid
%%{init: {'themeVariables': {'fontSize': '24px'}}}%%
flowchart TD
    UI[Frontend Web]
    SC[Smart Contract]
    BC[Blockchain]
    DB[(Database)]
    IPFS[(IPFS)]

    UI --> SC
    SC --> BC
    UI --> DB
    UI --> IPFS
```

</div>

---

# Consens

---

<div style="width:60%; margin:auto;">

```mermaid
%%{init: {'themeVariables': {'fontSize': '24px'}}}%%
flowchart TD
    CONS[Consens]
    CONS --> POW[Proof of Work]
    CONS --> POS[Proof of Stake]
    CONS --> DPOS[Delegated PoS]
    CONS --> BFT[BFT]
```

</div>

---

# Merkle Tree

---

<div style="width:60%; margin:auto;">

```mermaid
%%{init: {'themeVariables': {'fontSize': '24px'}}}%%
flowchart TD
    T1[Tx1]
    T2[Tx2]
    T3[Tx3]
    T4[Tx4]

    H1[Hash]
    H2[Hash]

    ROOT[Merkle Root]

    T1 --> H1
    T2 --> H1
    T3 --> H2
    T4 --> H2

    H1 --> ROOT
    H2 --> ROOT
```

</div>

---

# Resum

Blockchain és:

- registre distribuït
- immutable
- verificable criptogràficament

Aplicacions:

- criptomonedes
- DeFi
- NFTs
- DAOs
- tokenització d'actius
