``` mermaid
flowchart TB

    subgraph C["CZYTELNIK"]
        A["Wyszukaj i wybierz książkę"]
        B["Zanieś książkę bibliotekarzowi"]
        O["Odbierz książkę"]
    end

    subgraph L["BIBLIOTEKARZ"]
        D["Zeskanuj kartę czytelnika"]
        E["Zeskanuj kod egzemplarza"]
        H["Poinformuj o odmowie"]
        K["Poinformuj o rezerwacji"]
        N["Wydaj książkę czytelnikowi"]
    end

    subgraph S["SYSTEM"]
        F["Zweryfikuj uprawnienia"]
        G{"Czytelnik uprawniony?"}
        I["Sprawdź dostępność"]
        J{"Książka dostępna?"}
        P["Zarejestruj wypożyczenie"]
    end

    subgraph DB["BAZA DANYCH"]
        R[("Sprawdź stan egzemplarza")]
        T[("Zapisz wypożyczenie")]
    end

    START((START))
    STOP((KONIEC))

    START --> A
    A --> B
    B --> D
    D --> E
    E --> F
    F --> G

    G -->|NIE| H
    H --> STOP

    G -->|TAK| I
    I --> R
    R --> J

    J -->|NIE| K
    K --> STOP

    J -->|TAK| P
    P --> T
    T --> N
    N --> O
    O --> STOP

    classDef czytelnik fill:#d5f5e3,stroke:#27ae60,color:#000
    classDef bibliotekarz fill:#d6eaf8,stroke:#2980b9,color:#000
    classDef system fill:#ebdef0,stroke:#8e44ad,color:#000
    classDef baza fill:#fdebd0,stroke:#e67e22,color:#000
    classDef decyzja fill:#fadbd8,stroke:#c0392b,color:#000
    classDef punkt fill:#34495e,stroke:#2c3e50,color:#fff

    class A,B,O czytelnik
    class D,E,H,K,N bibliotekarz
    class F,I,P system
    class R,T baza
    class G,J decyzja
    class START,STOP punkt

    style C fill:transparent,stroke:#27ae60
    style L fill:transparent,stroke:#2980b9
    style S fill:transparent,stroke:#8e44ad
    style DB fill:transparent,stroke:#e67e22
```
