graph TD
    START((START))

    A["Gracz uruchamia gre"]
    B["System wczytuje poziom"]
    C["Gracz steruje postacia WASD"]
    D["Bohater porusza sie po labiryncie"]
    E["System sprawdza kolizje"]
    F{"Czy nastapila kolizja?"}
    G["Utrata zycia"]
    H{"Czy gracz ma zycia?"}
    I["Gracz zbiera monety"]
    J["System dodaje punkty"]
    K["Gracz szuka klucza"]
    L{"Czy znaleziono klucz?"}
    M["Gracz dociera do drzwi"]
    N["System otwiera drzwi"]
    O{"Czy to poziom trzeci?"}
    P["Wczytaj kolejny poziom"]
    R["Gracz wygrywa"]
    S["Koniec gry"]
    STOP((KONIEC))

    START --> A
    A --> B
    B --> C
    C --> D
    D --> E
    E --> F

    F -->|Tak| G
    G --> H
    H -->|Nie| S
    H -->|Tak| C

    F -->|Nie| I
    I --> J
    J --> K
    K --> L

    L -->|Nie| C
    L -->|Tak| M

    M --> N
    N --> O

    O -->|Nie| P
    P --> B

    O -->|Tak| R
    R --> STOP
    S --> STOP

    classDef gracz fill:#D5F5E3,stroke:#27AE60,color:#000000
    classDef bohater fill:#D6EAF8,stroke:#2980B9,color:#000000
    classDef system fill:#EBDEF0,stroke:#8E44AD,color:#000000
    classDef decyzja fill:#FADBD8,stroke:#C0392B,color:#000000
    classDef koniec fill:#34495E,stroke:#2C3E50,color:#FFFFFF

    class A,C,I,K,M gracz
    class D bohater
    class B,E,G,J,N,P,R,S system
    class F,H,L,O decyzja
    class START,STOP koniec
