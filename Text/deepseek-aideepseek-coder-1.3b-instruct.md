提示词模板 打分机制

![image-20250721164535682](C:/Users/LENOVO/AppData/Roaming/Typora/typora-user-images/image-20250721164535682.png)





Moonshot Kimi 

![image-20250721153122225](C:/Users/LENOVO/AppData/Roaming/Typora/typora-user-images/image-20250721153122225.png![image-20250721164428109](C:/Users/LENOVO/AppData/Roaming/Typora/typora-user-images/image-20250721164428109.png)

![image-20250721164659464](C:/Users/LENOVO/AppData/Roaming/Typora/typora-user-images/image-20250721164659464.png)



deepseek

![image-20250722133622963](C:/Users/LENOVO/AppData/Roaming/Typora/typora-user-images/image-20250722133622963.png)

![image-20250722133541946](C:/Users/LENOVO/AppData/Roaming/Typora/typora-user-images/image-20250722133541946.png)



qwen3

![image-20250722154843129](C:/Users/LENOVO/AppData/Roaming/Typora/typora-user-images/image-20250722154843129.png)



![image-20250722154823549](C:/Users/LENOVO/AppData/Roaming/Typora/typora-user-images/image-20250722154823549.png)



前期可以通过API快速验证 

API调用 ：优先qwen3 ,Kimi           deepseek太慢了api （4到5秒） ，国外模型的不稳定 需要翻墙



本地微调模型 Qwen1.5-7B结合 DeepSeek R17B



| 模块                       | 评价                                                         |
| -------------------------- | ------------------------------------------------------------ |
| 1. **简历解析器**          | 用 Qwen1.5-7B 负责结构化字段提取非常合适，Qwen 对中文理解和文本结构处理都很强，基础数据抽取稳定可靠。 |
| 2. **术语标准化/改写**     | 用 DeepSeek R7B 模型参数多，生成质量和专业度更高，特别适合精准改写和术语升级。资源允许的情况下推荐。 |
| 3. **JD-简历语义匹配评分** | Qwen1.5-7B 作为主模型做匹配和评分很合适，支持 LoRA 微调，且理解能力出色，能做细粒度匹配和缺项提示。 |
| 4. **智能简历生成器**      | 用 Qwen1.5-7B 生成简历符合其强大的文本生成和上下文理解优势，任务综合度高，表现更稳定。 |
|                            |                                                              |



| 模型                   | 参数量 | 4bit推理显存 | LoRA增量 | 微调总显存     |
| ---------------------- | ------ | ------------ | -------- | -------------- |
| Qwen1.5-7B             | 7B     | ≈ 5~6 GB     | ≈ 1~2 GB | ≈ **10~12 GB** |
| DeepSeek R1-7B         | 7B     | ≈ 5~6 GB     | ≈ 1~2 GB | ≈ **10~12 GB** |
| 👉 **总共（理想估算）** |        |              |          | ≈ **20~24 GB** |
| 👉 **总共（实际峰值）** |        |              |          | ≈ **26~30 GB** |
