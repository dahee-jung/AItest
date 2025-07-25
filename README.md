flowchart TD
    A[프로필 선택] --> B[살아있는 영어 실행]
    B --> C{업데이트 이후<br/>첫 실행인가?}
    
    C -->|YES| D{이전 튜토리얼<br/>성공했나?}
    C -->|NO| P[월드맵 진입]
    
    D -->|성공| P
    D -->|실패 or 미진행| E[튜토리얼 시작]
    
    E --> F[월드맵 dim 처리<br/>게이트 UI 출력]
    F --> G[안내 메시지 출력<br/>'살아있는 영어로 들어가기 위한<br/>주문을 말해보세요!']
    G --> H[발화 문장 제시<br/>'Look at me' 등]
    H --> I[문장 음성 출력]
    I --> J[블루 버튼 UI 출력<br/>발화 대기]
    
    J --> K[사용자 발화]
    K --> L{발화 성공?}
    
    L -->|성공| M[성공 연출<br/>효과음 + UI 변경]
    M --> N[성공 안내 멘트<br/>'잘했어요! Let's go!']
    N --> O[튜토리얼 UI 삭제<br/>dim 해제]
    O --> P
    
    L -->|실패| Q{실패 횟수<br/>확인}
    Q -->|1회차 실패| R[실패 유형별<br/>피드백 제공]
    Q -->|2회차 실패| S[튜토리얼 실패 처리]
    
    R --> T[피드백 멘트 출력<br/>- 볼륨 관련<br/>- 중복 발화<br/>- 조기 발화<br/>- 다른 문장]
    T --> U[문장 재출력]
    U --> J
    
    S --> V[실패 안내 멘트<br/>'제플린과 얘기할 때는...'<br/>당부 멘트]
    V --> W[튜토리얼 UI 삭제<br/>dim 해제]
    W --> P
    
    P --> END[메인 콘텐츠<br/>이용 가능]
    
    style A fill:#e1f5fe
    style B fill:#e1f5fe
    style E fill:#fff3e0
    style M fill:#e8f5e8
    style R fill:#ffebee
    style S fill:#ffebee
    style P fill:#f3e5f5
    style END fill:#f3e5f5
