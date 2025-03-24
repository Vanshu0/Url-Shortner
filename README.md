flowchart LR
    subgraph A[Clients]
        A1[Client 1] --> B[Auth Service]
        A2[Client 2] --> B
        AN[Client N] --> B
    end

    B --> C[/url.. request/]
    C --> D[URL Getter]

    subgraph E[URL Generation Service]
        F[Duplicate Checker] --> G[Short ID Generator]
    end
    D --> F

    subgraph H[DB]
    end

    F --> H
    G --> H

    subgraph I[URL Redirection Service]
        J[Check Existence] --> K[Redirector]
    end

    D --> J
    J --> H
    K --> L[Original Host]
