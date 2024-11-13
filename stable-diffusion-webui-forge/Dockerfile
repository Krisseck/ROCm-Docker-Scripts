FROM rocm/pytorch:rocm6.2.3_ubuntu22.04_py3.10_pytorch_release_2.3.0

RUN apt-get update && \
    apt-get install --no-install-recommends -y google-perftools bc && \
    rm -rf /var/lib/apt/lists/*

RUN git clone --depth 1 https://github.com/lllyasviel/stable-diffusion-webui-forge.git /app

WORKDIR /app

# Fix some dependencies
RUN pip install -r requirements_versions.txt
RUN pip install --upgrade insightface botocore>=1.29.153 boto3>=1.26.153

# Use global python env
RUN sed -i -e 's/use_venv=1/use_venv=0/g' webui.sh
# Allow running as root
RUN sed -i -e 's/can_run_as_root=0/can_run_as_root=1/g' webui.sh

ENTRYPOINT ["/app/webui.sh", "--listen"]
