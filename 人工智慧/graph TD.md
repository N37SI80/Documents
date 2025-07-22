graph TD
    subgraph 1. 訓練與匯出 (Training & Export)
        A[PyTorch / TensorFlow 等訓練框架] -->|匯出為標準格式| B(模型檔案.onnx);
    end

    subgraph 2. 推論引擎 (Inference Engine)
        B --> C{ONNX Runtime};
        subgraph C
            D[<b style='color: #D9534F;'>Execution Provider<br>(執行提供者)</b>]
        end
    end

    subgraph 3. 硬體層 (Hardware Layer)
        D -->|選擇 CUDA EP| E[NVIDIA GPU (CUDA)];
        D -->|選擇 ROCm EP| F[AMD GPU (ROCm)];
        D -->|選擇 CPU EP| G[CPU (Intel/AMD)];
        D -->|選擇其他 EP| H[更多硬體... (如 NPU, FPGA)];
    end

    style D fill:#fcf,stroke:#D9534F,stroke-width:3px