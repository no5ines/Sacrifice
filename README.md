```mermaid
graph TD
    %% 定义样式，让不同类型的节点更易区分
    classDef feeling fill:#f9f,stroke:#333,stroke-width:2px;
    classDef action fill:#ccf,stroke:#333,stroke-width:2px;
    classDef decision fill:#cfc,stroke:#333,stroke-width:2px;
    classDef state fill:#ffc,stroke:#333,stroke-width:2px;
    classDef outcome fill:#ddd,stroke:#333,stroke-width:2px;
    classDef conflict fill:#f66,stroke:#333,stroke-width:2px;

    %% 子图1: 初始状态与潜在需求
    subgraph "阶段一: 内在渴望与戒备 (Initial Stage)"
        A(感到需要连结):::feeling --> B{遇到潜在关系对象?};
        B -- 是 --> C[尝试谨慎接近/观察];
        B -- 否 --> D(停留在舒适圈):::state;
    end

    %% 子图2: 互动与风险感知
    subgraph "阶段二: 互动与风险评估 (Interaction & Risk Assessment)"
        C --> E(分享一点脆弱):::action;
        E --> F{得到积极/理解回应?};
        F -- 是 --> G(感到一丝安全):::feeling;
        F -- 否 --> H(感到不安全/被误解):::feeling;
    end

    %% 子图3: 信任建立路径
    subgraph "路径 A: 信任渐增 (Trust Building Path)"
        G --> I[决定再多开放一些]:::action;
        I --> J{关系持续正面互动?};
        J -- 是 --> K(信任度提升):::state;
        K --> L[进入更深层互动]:::action;
        L --> M((建立稳固联结)):::outcome;
        K --> J; %% 信任提升可能带来持续正面互动
end

    %% 子图4: 应对不安全路径
    subgraph "路径 B: 应对不安全感 (Handling Insecurity Path)"
        H --> N{如何应对不安全感?};
        N -- "退缩/关闭" --> O[减少开放/保持距离]:::action;
        O --> P(回到戒备状态):::state;
        P --> Q((关系停滞/疏远)):::outcome;

        N -- "试图沟通/澄清" --> R[表达感受/疑虑]:::action;
        R --> S{沟通是否有效?};
        S -- 是 --> T(误会消除/理解增进):::state;
        T --> G; %% 理解增进可能导向安全感提升，回到路径 A
        S -- 否 --> H; %% 沟通无效可能强化不安全感，停留在路径 B
    end

    %% 连接不同子图和路径
    D --> A; %% 停留在舒适圈后可能再次感到连结需求
    Q --> A; %% 关系疏远后可能再次感到连结需求
    M --> A; %% 稳固联结后可能出现新的脆弱或需求，进入新的循环或阶段 (这里简化连接回开始)

    P --> Q; %% 戒备状态可能直接导向关系疏远
    O --> P; %% 减少开放会强化戒备状态

    %% 引入一个更复杂的内部冲突点
    subgraph "内在冲突点 (Internal Conflict)"
        conflict_node("害怕失去自我 vs 渴望亲密"):::conflict;
        L --> conflict_node; %% 深度互动可能触发此冲突
        O --> conflict_node; %% 减少开放也是此冲突的表现
        T --> conflict_node; %% 即使理解增进，冲突依然存在
    end

    conflict_node --> N; %% 内在冲突影响如何应对不安全感 (回到路径 B 的决策点)
    conflict_node --> I; %% 内在冲突也影响是否决定多开放 (回到路径 A 的决策点)

    %% 最终可能状态的集合 (作为示例的简化终点)
    subgraph "可能的长期状态 (Potential Long-term States)"
        EndA((更深的连结)):::outcome;
        EndB((保持距离/浅层关系)):::outcome;
        EndC((关系结束)):::outcome;
    end

    M --> EndA;
    Q --> EndB;
    Q --> EndC;
    P --> EndB;
    H --> EndC; %% 持续不安全感可能导致关系破裂
