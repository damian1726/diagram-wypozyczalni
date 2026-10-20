---
config:
  theme: base
  themeVariables:
    background: "transparent"
  themeCSS: |
    svg {
      background: transparent !important;
    }
    .cluster rect {
      fill: transparent !important;
    }
---
flowchart TD

    START((START))

    subgraph C["CZYTELNIK"]
        A(["Wyszukaj i wybierz książkę"])
        B["Zanieś książkę bibliotekarzowi"]
        M(["Odbierz książkę"])
    end

    subgraph L["BIBLIOTEKARZ"]
        D[/"Zeskanuj kartę czytelnika"/]
        E[/"Zeskanuj kod egzemplarza"/]
        H["Poinformuj o odmowie"]
        K["Poinformuj o rezerwacji"]
        N["Wydaj książkę czytelnikowi"]
    end

    subgraph S["SYSTEM"]
        F["Zweryfikuj uprawnienia"]
        G{"Uprawniony?"}
        I["Sprawdź dostępność"]
        J{"Dostępny?"}
        O["Zarejestruj wypożyczenie"]
    end

    subgraph DB["BAZA DANYCH"]
        P[("Sprawdź stan egzemplarza")]
        R[("Zapisz wypożyczenie")]
    end

    KONIEC((KONIEC))

    START --> A
    A --> B
    B --> D
    D --> E
    E --> F
    F --> G

    G -->|NIE| H
    H --> KONIEC

    G -->|TAK| I
    I --> P
    P --> J

    J -->|NIE| K
    K --> KONIEC

    J -->|TAK| O
    O --> R
    R --> N
    N --> M
    M --> KONIEC

    classDef czytelnik fill:#C8E6C9,stroke:#388E3C,stroke-width:2px,color:#1B5E20;
    classDef bibliotekarz fill:#BBDEFB,stroke:#1976D2,stroke-width:2px,color:#0D47A1;
    classDef system fill:#E1BEE7,stroke:#8E24AA,stroke-width:2px,color:#4A148C;
    classDef baza fill:#FFE0B2,stroke:#F57C00,stroke-width:2px,color:#E65100;
    classDef decyzja fill:#F8BBD0,stroke:#D81B60,stroke-width:3px,color:#880E4F;
    classDef start fill:#37474F,stroke:#263238,stroke-width:2px,color:#FFFFFF;

    class A,B,M czytelnik;
    class D,E,H,K,N bibliotekarz;
    class F,I,O system;
    class P,R baza;
    class G,J decyzja;
    class START,KONIEC start;

    style C fill:transparent,stroke:#66BB6A,stroke-width:2px
    style L fill:transparent,stroke:#42A5F5,stroke-width:2px
    style S fill:transparent,stroke:#AB47BC,stroke-width:2px
    style DB fill:transparent,stroke:#FFA726,stroke-width:2px+
