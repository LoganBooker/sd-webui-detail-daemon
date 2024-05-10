# Detail Daemon
This is an extension for [Stable Diffusion Web UI](https://github.com/AUTOMATIC1111/stable-diffusion-webui), which allows users to adjust the amount of detail in an image, during the sampling steps. 

It works by manipulating the noise levels (sigmas) during the sampling process, effectively telling the model to denoise more or less aggressively at given steps. So it uses no LORAs, ControlNets etc. and as a result it's performance is not biased towards any certain style and introduces no new stylistic or semantic features into your generation. This also means that it can work with any model and on any type of image.

![a close up portrait of a cyberpunk knight-1Lv-0](https://github.com/muerrilla/sd-webui-detail-daemon/assets/48160881/561c33d9-9a5d-4cfc-bee8-de9126b280c1)
*Left: Less detail, Middle: Original, Right: More detail*<br>
*Model: SSD-1B*<br>

![face of a cute cat love heart symbol-Zn6-0](https://github.com/muerrilla/sd-webui-detail-daemon/assets/48160881/9fbfb39f-81fb-4951-8f32-20eab410020a)
*Left: Less detail, Middle: Original, Right: More detail*<br>
*Model: SD 1.5 (custom finetuned)*<br>
## Installation
Open SD WebUI > Go to Extensions tab > Go to Install from URL > Paste this repo's URL into the first field > Click Install

Or go to your WebUI folder and manually clone this repo into your extensions folder:

`git clone "https://github.com/muerrilla/sd-webui-detail-daemon" extensions/stable-diffusion-NPW`

Note: You might need to shut down SD WebUI and start it again for the dependencies to install.

## Getting Started
After installation you can find the extension in your txt2img and img2img tabs. 

![2024-05-10 23_28_38-011344](https://github.com/muerrilla/sd-webui-detail-daemon/assets/48160881/752c9fc6-fad7-40e2-824a-62d9fee12fae)

These controls allow you to set the amount of adjustment (positive values → more detail, negative values → less detail) and the sampling steps during which it is applied. So the X axis of the graph is your sampling steps, normalized to the (0,1) range, and the Y axis is the amount of adjustment, and all the sliders do is affect the shape of your schedule.

I'll write up some proper docs on how best to set the parameters, as soon as possible.

For now you gotta play around with the sliders and figure out how the shape of the schedule affects the image. I suggest you set your live preview period period to every frame, or every other frame if that's not possible, so you could see clearly what's going on at every step of the sampling process and how Detail Daemon affects it, till you get a good grasp of how this thing works.

## Notes:
- Doesn't work with all samplers at the moment (e.g. DPM++ SDE Karras), but works with the main good ones. Will fix this.
- It's probably impossible to use or very hard to control with few-step models (Turbo, Lightning, etc.).
- It was built and tested on SD Webui 1.8.0, so hope it works fine on the newer releases.
- Yes, it works with forge.
- No, it's not the same as AlignYourSteps, FreeU, etc.
- It is similar (in what it sets out to do, not in how it does it) to the [ReSharpen Extension](https://github.com/Haoming02/sd-webui-resharpen) by Haoming.
- This is WIP and subject to change.