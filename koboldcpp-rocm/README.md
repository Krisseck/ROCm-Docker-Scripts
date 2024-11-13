# Build

It's *REALLY* important that you set the `BUILD_TARGETS` correctly! Otherwise the project won't build.

`docker build -t koboldcpp-rocm:latest --build-arg BUILD_TARGETS=gfx1100 ./`

# Run

`docker run --rm -it --device /dev/kfd:/dev/kfd --device /dev/dri:/dev/dri -p 7860:7860 -v /path/to/your/models:/app/models koboldcpp-rocm:latest [optional arguments here] /app/models/your-model.gguf`
