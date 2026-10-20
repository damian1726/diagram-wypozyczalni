flowchart TD

    START((START))

    subgraph A["GRACZ"]
        A1["Uruchom grę"]
        A2["Steruj postacią klawiszami W A S D"]
        A3["Przejdź do kolejnego poziomu"]
        A4["Zakończ grę"]
    end

    subgraph B["BOHATER"]
        B1["Rozpocznij poruszanie po labiryncie"]
        B2["Omijaj ściany i przeszkody"]
        B3["Zbieraj monety"]
        B4["Znajdź i podnieś klucz"]
        B5["Dotrzyj do drzwi wyjściowych"]
    end

    subgraph C["SYSTEM GRY"]
        C1["Wczytaj poziom"]
        C2["Sprawdź kolizje"]
        C3["Dodaj punkty za monety"]
        C4{"Czy gracz ma klucz?"}
        C5["Otwórz drzwi"]
        C6{"Czy gracz ma życie i czas?"}
        C7["Zakończ rozgrywkę"]
    end

    subgraph D["POZIOMY GRY"]
        D1["Poziom 1 - prosty labirynt"]
        D2["Poziom 2 - ruchome przeszkody"]
        D3["Poziom 3 - przeciwnik i limit czasu"]
        D4{"Czy ukończono wszystkie poziomy?"}
        D5["Wygrana"]
    end

    KONIEC((KONIEC))

    START --> A1
    A1 --> C1
    C1 --> D1
    D1 --> A2
    A2 --> B1
    B1 --> B2
    B2 --> C2
    C2 --> C6

    C6 -->|NIE| C7
    C7 --> KONIEC

    C6 -->|TAK| B3
    B3 --> C3
    C3 --> B4
    B4 --> B5
    B5 --> C4

    C4 -->|NIE| B4
    C4 -->|TAK| C5

    C5 --> D4

    D4 -->|NIE| A3
    A3 --> D2
    D2 --> D3
    D3 --> C1

    D4 -->|TAK| D5
    D5 --> A4
    A4 --> KONIEC

    classDef gracz fill:#D5F5E3,stroke:#27AE60,color:#000
    classDef bohater fill:#D6EAF8,stroke:#2980B9,color:#000
    classDef system fill:#EBDEF0,stroke:#8E44AD,color:#000
    classDef poziomy fill:#FDEBD0,stroke:#E67E22,color:#000
    classDef decyzja fill:#FADBD8,stroke:#C0392B,color:#000
    classDef punkt fill:#34495E,stroke:#2C3E50,color:#fff

    class A1,A2,A3,A4 gracz
    class B1,B2,B3,B4,B5 bohater
    class C1,C2,C3,C5,C7 system
    class D1,D2,D3,D5 poziomy
    class C4,C6,D4 decyzja
    class START,KONIEC punkt

    style A fill:transparent,stroke:#27AE60
    style B fill:transparent,stroke:#2980B9
    style C fill:transparent,stroke:#8E44AD
    style D fill:transparent,stroke:#E67E22
