``` mermaid
flowchart TD
    A([START])
    B[Uruchom grę]
    C[Wczytaj poziom]
    D[Poruszaj się klawiszami WASD]
    E[Omijaj ściany i przeszkody]
    F[Zbieraj monety i zdobywaj punkty]
    G{Czy znaleziono klucz?}
    H[Kontynuuj poszukiwania]
    I[Dotrzyj do drzwi]
    J[Otwórz drzwi]
    K{Czy ukończono 3 poziomy?}
    L[Przejdź do kolejnego poziomu]
    M[Wygrana]
    N([KONIEC])

    A --> B
    B --> C
    C --> D
    D --> E
    E --> F
    F --> G
    G -->|NIE| H
    H --> D
    G -->|TAK| I
    I --> J
    J --> K
    K -->|NIE| L
    L --> C
    K -->|TAK| M
    M --> N

    classDef gracz fill:#d5f5e3,stroke:#27ae60,color:#000
    classDef system fill:#d6eaf8,stroke:#2980b9,color:#000
    classDef decyzja fill:#fadbd8,stroke:#c0392b,color:#000

    class B,D,E,F,H,I gracz
    class C,J,L,M system
    class G,K decyzja
```
