flowchart LR
  U[User/Bidder] -->|Web/Mobile| G[API Gateway]
  S[Seller] -->|Web/Mobile| G

  G --> A[Auth & User Service]
  G --> C[Catalog Service]
  G --> B[Auction/Bidding Service]
  G --> W[Wallet Service]

  B -->|publish events| EB[(Event Bus / Message Broker)]
  EB --> RT[Realtime Gateway (WS/SSE)]
  EB --> N[Notification Service]
  EB --> C

  RT -->|push updates| U
  N -->|email/push/in-app| U
