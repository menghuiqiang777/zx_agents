# zx_agents

`zx_agents` 是一个针对 OpenAI 代理定制的 Python 包，提供了多种模型支持和流处理功能。本 README 将介绍该包的功能、安装方法、使用前置条件和使用示例。

## 安装
使用 `pip` 可以轻松安装 `zx_agents` 包：
```bash
pip install zx_agents
from zx_agents import agent_stream_processor, provider_model, test_agent

使用前置条件

    设置/etc/environment,设置
    ARK_API_KEY       #火山引擎
    QWEN_API_KEY      #阿里通义
    DEEPSEEK_API_KEY  #DeepSeek 

## 使用示例

from zx_agents import agent_stream_processor, provider_model, test_agent

model_ark = provider_model.ModelArk().get_model()



样例
···python
if __name__ == "__main__":
    import asyncio
    from agents import Agent, Runner,RunConfig
   
    from zx_agents  import ModelArk,ModelQwen,ModelDeepSeek
    def get_models():
        models = []
        models.append(ModelArk().get_model())
        models.append(ModelQwen("qwen-max").get_model())
        models.append(ModelDeepSeek().get_model())
        models.append(ModelDeepSeek("deepseek-reasoner").get_model())
        return models

    def new_agent(model):
        agent = Agent(
            name="Assistant",
            instructions="You are helpful assistant",
            model=model,
        )
        return agent
    async def main():
        models = get_models()
        for model in models:
            agent = new_agent(model)
            result = await Runner.run(agent, "你是谁？")
            print(result.final_output)
    asyncio.run(main())


  参考：https://www.yuque.com/u10030287/gwa/byx5thhxpozdyzx6  