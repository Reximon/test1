# Architecture Overview

```mermaid
flowchart TB
    subgraph Users[Users]
        User[User / Client]
    end

    subgraph Application[Application]
        UI[Frontend]
        API[Backend API]
        Worker[Background Worker]
    end

    subgraph Data[Data and Services]
        DB[(Database)]
        Cache[(Cache)]
        Storage[(Object Storage)]
        External[External Services]
    end

    User -->|HTTPS| UI
    UI -->|API requests| API
    API -->|Read / write| DB
    API -->|Cache lookup| Cache
    API -->|Upload / download| Storage
    API -->|Publish jobs| Worker
    Worker -->|Read / write| DB
    Worker -->|Call APIs| External
```

## Components

- **Frontend:** Provides the user interface and communicates with the backend API.
- **Backend API:** Handles requests, business logic, authentication, and integrations.
- **Background Worker:** Processes asynchronous jobs and scheduled tasks.
- **Database:** Stores persistent application data.
- **Cache:** Improves performance by storing frequently accessed data.
- **Object Storage:** Stores files and other unstructured data.
- **External Services:** Provides third-party integrations and APIs.
