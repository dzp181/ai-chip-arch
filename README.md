# AI 芯片架构专家（AI Chip Architecture Expert）

AI 芯片架构设计专家：从负载画像出发，完成算力阵列与数据流设计、存储层次与带宽预算、片上互联、量化精度架构、模型-硬件协同设计与 PPA 取舍，覆盖训练卡与大模型推理芯片的完整架构推导。

## 类型

Agent 型（单个 AI 专家）

## 功能

- **算力阵列与数据流**：MAC 阵列组织（SIMD / SIMT / 脉动阵列 / 张量核）、PE 维度映射与数据复用率、权重/激活/输出驻留策略、流水切分、2:4 结构化稀疏落法、矩阵乘/卷积/注意力各类算子的硬件映射差异。
- **存储层次与带宽预算**：SRAM / Tensor RAM / HBM / DDR 多级容量与带宽分配、权重驻留容量核算、KV Cache 容量与带宽、算子融合消除中间结果、tile 尺寸与带宽算力平衡点。
- **片上互联与 NoC**：mesh / ring / crossbar 拓扑选型、仲裁与拥塞控制、QoS 与 VC、MoE 与 attention 的 all-to-all 流量特征、die-to-die 与 chiplet 互联。
- **量化与精度架构**：INT8 / INT4 / FP8 / FP4 选型、per-channel 与 per-group 粒度、累加精度、离群值处理、PTQ 与 QAT 的硬件要求、KV Cache 量化。
- **模型-硬件协同设计**：从模型结构反推算术强度与访存量、GQA/MQA 与 FlashAttention 式融合的硬件诉求、MoE 专家并行代价、投机解码与 Medusa 的硬件友好性、编译器融合配合点。
- **性能建模与瓶颈分析**：Roofline 与算术强度、实测吞吐与峰值差距的归因（带宽 / 算子覆盖 / 调度 / 启动开销）、TTFT 与 TPOT 分解、每瓦 token 推算。
- **PPA 取舍**：面积分解（阵列 / SRAM / 寄存器 / NoC / 控制）、数据搬运功耗主导规律、频率与阵列规模的可综合性、chiplet 拆分对良率与 PPA 的实际影响、散热与功耗墙。
- **SoC 与系统集成**：CPU/NPU 分区与一致性、共享内存、任务调度与驱动栈、DMA 零拷贝、编译栈对接、多模型与多租户支持、性能计数器与可观测性。

## 使用示例

- 我要做一颗大模型推理芯片，目标 70B 模型 INT4、单请求 TTFT 100ms 以内，请从算力阵列、存储带宽、KV Cache 到互联给我一套架构方案和瓶颈推导。
- 我们的 INT4 张量核算力有 200 TOPS，但端到端吞吐只有峰值的 18%，帮我判断瓶颈是内存带宽、NoC 争抢、kernel 启动开销还是数据流调度不理想。
- 对比三种 7B 大模型服务芯片架构：统一张量核阵列、注意力引擎加 MLP 专用阵列、权重静止脉动阵列，给出 PPA 与吞吐的取舍。

## 头像

头像已自动生成在 `avatars/` 目录下。如需替换为自定义头像，要求：
- 格式：PNG（推荐）或 JPG
- 尺寸：512×512 px
- 大小：单张不超过 500KB

## 安装

将专家包目录放到专家目录下：

```
/Users/dzp/.workbuddy/plugins/marketplaces/my-experts/plugins/ai-chip-arch/
```

然后运行注册命令使其可见：

```bash
python3 scripts/register_expert.py <expert-dir>
```

## 打包分享

```bash
python3 scripts/package_expert.py <expert-dir>
```
