 # 使用 Anaconda3 为基础镜像
FROM continuumio/anaconda3

# 设置工作目录
WORKDIR /app

# 复制当前目录 (i.e. 你的项目) 到工作目录
COPY . /app

# 创建 conda 环境
RUN conda env create -f environment.yml

# 激活新创建的环境
RUN echo "source activate $(head -1 environment.yml | cut -d' ' -f2)" > ~/.bashrc
ENV PATH /opt/conda/envs/$(head -1 environment.yml | cut -d' ' -f2)/bin:$PATH

# 设置环境变量，使 python 输出不会在 docker 日志中被缓冲
ENV PYTHONUNBUFFERED=1

# 运行你的项目
CMD ["python", "app_gradio.py"]