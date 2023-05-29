```mermaid
flowchart TB
 A((Registro de soldados)) -->|Verificar| B{Soldado registrado?}
    B -- Sí --> C((Generación de códigos QR))
    C -- Verificar --> D{Código QR generado?}
    D -- Sí --> E((Escaneo de códigos QR para asignación))
    E -- Verificar --> F{Código QR válido?}
    F -- Sí --> G((Registro de datos de asignación))
    F -- No --> E
    G -- Devolución --> H((Devolución de fusiles))
    H -- Verificar --> I{Fusil devuelto?}
    I -- Sí --> J((Escaneo de códigos QR para devolución))
    J -- Verificar --> K{Código QR válido?}
    K -- Sí --> L((Registro de datos de devolución))
    K -- No --> M((Manejo de error de QR de devolución))
    M --> H
    L -- Verificar --> N{Fusil en buen estado?}
    N -- Sí --> O((Verificación y control de estado))
    N -- No --> P((Reparación del fusil))
    P --> L
    O -- Nuevo fusil asignado --> G
    O -- Fusil no asignado --> Q((Fin del proceso))
    B -- No --> R((Registro del soldado))
    R --> A
    D -- No --> S((Generación de código QR fallida))
    S --> T((Manejo de error))
    T --> D
    F -- Error --> U((Código QR inválido))
    U --> E
    J -- Error --> V((Código QR de devolución inválido))
    V --> M
