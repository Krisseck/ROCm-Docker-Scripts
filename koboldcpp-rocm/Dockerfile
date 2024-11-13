FROM rocm/dev-ubuntu-24.04:6.2.4-complete

RUN apt-get update && apt-get install --no-install-recommends -y git && rm -rf /var/lib/apt/lists/*

RUN git clone --depth 1 https://github.com/YellowRoseCx/koboldcpp-rocm.git /app 

WORKDIR /app        

ARG BUILD_THREADS=4
ARG BUILD_TARGETS=gfx1100

RUN make LLAMA_HIPBLAS=1 GPU_TARGETS=${BUILD_TARGETS} -j${BUILD_THREADS}

ENTRYPOINT ["python3", "koboldcpp.py", "--usecublas", "--port", "7860"]


