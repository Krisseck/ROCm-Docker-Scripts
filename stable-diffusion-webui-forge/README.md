# Build

`docker build -t stable-diffusion-webui-forge:latest ./`

# Run

`docker run --rm -it --device /dev/kfd:/dev/kfd --device /dev/dri:/dev/dri -v /path/to/your/models:/app/models -p 7860:7860 stable-diffusion-webui-forge:latest`
