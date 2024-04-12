# face-to-many

Turn any face into 3D, pixel art, video game, claymation or toy.

Run this model on Replicate:

https://replicate.com/fofr/face-to-many

Or run it in ComfyUI:

https://github.com/fofr/cog-face-to-many/blob/main/face-to-many-ui.json

You’ll need these custom nodes:

- [ComfyUI Controlnet Aux](https://github.com/Fannovel16/comfyui_controlnet_aux/tree/6d6f63c)
- [ComfyUI InstantID](https://github.com/cubiq/ComfyUI_InstantID/tree/0fcf494)
- [ComfyUI IPAdapter Plus](https://github.com/cubiq/ComfyUI_IPAdapter_plus/tree/4e898fe)
- [ComfyUI Essentials](https://github.com/cubiq/ComfyUI_essentials/tree/c9236fe)
- [Efficiency Nodes ComfyUI](https://github.com/jags111/efficiency-nodes-comfyui/tree/1ac5f18)

![Arnold](https://replicate.delivery/pbxt/R1ayGe5efoQbaoRzgDEJdLsIZ20lWRiprvoW1F4uKAZIha6kA/ComfyUI_00001_.png)

## Loras

The 3D, video game, pixel art, claymation and toy loras are all made by artificialguybr. If you like them you can make a donation to their Patreon or Ko-fi:

- https://www.patreon.com/user?u=81570187
- https://ko-fi.com/artificialguybr

Or follow him on Twitter:

https://twitter.com/artificialguybr

## Developing locally

Clone this repository:

```sh
git clone --recurse-submodules https://github.com/fofr/cog-face-to-many.git && cd cog-face-to-many/ComfyUI
```

Create python venv and activate

```sh
python3 -m venv . && source bin/activate
```

Install the required dependencies

```sh
pip install -r requirements.txt
```

Download albedobaseXL_v13.safetensors to models/checkpoints


```sh
wget https://huggingface.co/frankjoshua/albedobaseXL_v13/resolve/main/albedobaseXL_v13.safetensors?download=true -O models/checkpoints/albedobaseXL_v13.safetensors
```

Download antelopev2


```sh
git clone https://huggingface.co/DIAMONIK7777/antelopev2 models/insightface/models/antelopev2
```

Download instantid-ip-adapter.bin

```sh
wget https://huggingface.co/Aitrepreneur/InstantID-Controlnet/resolve/main/checkpoints/ip-adapter.bin?download=true -O models/instantid/instantid-ip-adapter.bin
```

Download instantid-controlnet.safetensors

```sh
wget https://huggingface.co/Aitrepreneur/InstantID-Controlnet/resolve/main/checkpoints/ControlNetModel/diffusion_pytorch_model.safetensors?download=true -O models/controlnet/instantid-controlnet.safetensors
```

Run the [following script](https://github.com/fofr/cog-face-to-many/blob/main/scripts/clone_plugins.sh) to install all the custom nodes:

```sh
./scripts/clone_plugins.sh
```

Finally, install it, run it and enjoy it!

```sh
python3 main.py
```

### Running the Web UI from your Cog container

1. **GPU Machine**: Start the Cog container and expose port 8188:
```sh
sudo cog run -p 8188 bash
```
Running this command starts up the Cog container and let's you access it

2. **Inside Cog Container**: Now that we have access to the Cog container, we start the server, binding to all network interfaces:
```sh
cd ComfyUI/
python main.py --listen 0.0.0.0
```

3. **Local Machine**: Access the server using the GPU machine's IP and the exposed port (8188):
`http://<gpu-machines-ip>:8188`

When you goto `http://<gpu-machines-ip>:8188` you'll see the classic ComfyUI web form!
