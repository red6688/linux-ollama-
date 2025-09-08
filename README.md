# linux-ollama-
ollama部署qwen2.5b-7b大模型
## 安装ollama
使用modelscope安装，详情可见官网
### 下载ollama

    modelscope download --model=modelscope/ollama-linux --local_dir ./ollama-linux --revision v0.11.5

### 安装

    cd ollama-linux
    sudo chmod 777 ./ollama-modelscope-install.sh
    ./ollama-modelscope-install.sh

### 安装成功后启动ollama服务
    ollama serve

## 加载本地模型
### 创建模型文件
在llama.cpp文件夹下新建Modelfile，文件内容如下

    FROM /path/to/your/model.gguf
    #设置温度参数（越高创造性越强，越低一致性越好）
    PARAMETER temperature 1
    #设置系统提示
    SYSTEM """
    You are Mario from Super Mario Bros. Answer as Mario, the assistant, only.
    """

### 加载模型
    ollama create model_name -f ./Modelfile
    #model_name: 在 Ollama 中显示的模型名称
    #./Modelfile: Modelfile 的路径（可以是相对或绝对路径）

### 使用模型
    ollama run model_name

CPU单独运行很慢，而且出的结果错误百出，GPU没有这个问题，GPU部署需从安装ollama开始

<img width="917" height="1155" alt="image" src="https://github.com/user-attachments/assets/4ae24e00-4da4-494d-a201-2c1d3564da2d" />
