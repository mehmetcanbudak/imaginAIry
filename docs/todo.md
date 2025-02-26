## Todo

### v14 todo

 - configurable composition cutoff
 - rename model parameter weights 
 - rename model_config parameter to architecture and make it case insensitive
 - add --size parameter that accepts strings (e.g. 256x256, 4k, uhd, 8k, etc)
 - detect if cuda torch missing and give better error message
 - add method to install correct torch version
 - allow selection of output video format
 - chain multiple operations together imggen => videogen
 - make sure terminal output on windows doesn't suck
 - add karras schedule to refiners
 - add method to show cache size
 - add method to clear model cache
 - add method to clear cached items not recently used (does diffusers have one?)

### Old Todo

 - Inference Performance Optimizations
   - ✅ fp16
   - ✅ [Doggettx Sliced attention](https://github.com/CompVis/stable-diffusion/compare/main...Doggettx:stable-diffusion:autocast-improvements#)
   - ✅ xformers support https://www.photoroom.com/tech/stable-diffusion-100-percent-faster-with-memory-efficient-attention/
   - https://github.com/neonsecret/stable-diffusion  
   - https://github.com/CompVis/stable-diffusion/pull/177
   - https://github.com/huggingface/diffusers/pull/532/files
   - https://github.com/HazyResearch/flash-attention
   - https://github.com/chavinlo/sda-node
   - https://github.com/AminRezaei0x443/memory-efficient-attention/issues/7
   
 - Development Environment
   - ✅ add tests
   - ✅ set up ci (test/lint/format)
   - ✅ unified pipeline (txt2img & img2img combined)
   - ✅ setup parallel testing
   - add docs
   - 🚫 remove yaml config
   - 🚫 delete more unused code
   - faster latent logging https://discuss.huggingface.co/t/decoding-latents-to-rgb-without-upscaling/23204/9
 - Interface improvements
   - ✅ init-image at command line
   - ✅ prompt expansion
   - ✅ interactive cli
 - Image Generation Features
   - ✅ add k-diffusion sampling methods
   - ✅ tiling
   - ✅ generation videos/gifs
   - ✅ controlnet
     - scribbles input
     - segmentation input
     - mlsd input
   - [Attend and Excite](https://attendandexcite.github.io/Attend-and-Excite/)
   - Compositional Visual Generation
     - https://github.com/energy-based-model/Compositional-Visual-Generation-with-Composable-Diffusion-Models-PyTorch
     - https://colab.research.google.com/github/energy-based-model/Compositional-Visual-Generation-with-Composable-Diffusion-Models-PyTorch/blob/main/notebooks/demo.ipynb#scrollTo=wt_j3uXZGFAS
   - ✅ negative prompting
     - some syntax to allow it in a text string
   - [paint with words](https://www.reddit.com/r/StableDiffusion/comments/10lzgze/i_figured_out_a_way_to_apply_different_prompts_to/)
     - https://github.com/cloneofsimo/paint-with-words-sd 
   - https://multidiffusion.github.io/
   - images as actual prompts instead of just init images. 
     - not directly possible due to model architecture.
     - can it just be integrated into sampler? 
     - requires model fine-tuning since SD1.4 expects 77x768 text encoding input
     - https://twitter.com/Buntworthy/status/1566744186153484288
     - https://github.com/justinpinkney/stable-diffusion
     - https://github.com/LambdaLabsML/lambda-diffusers
     - https://www.reddit.com/r/MachineLearning/comments/x6k5bm/n_stable_diffusion_image_variations_released/
 - Image Editing
   - ✅outpainting
     - https://github.com/parlance-zz/g-diffuser-bot/search?q=noise&type=issues
     - lama cleaner
   - ✅ inpainting
     - https://github.com/Jack000/glid-3-xl-stable 
     - https://github.com/andreas128/RePaint
     - ✅ img2img but keeps img stable
     - https://www.reddit.com/r/StableDiffusion/comments/xboy90/a_better_way_of_doing_img2img_by_finding_the/
     - https://gist.github.com/trygvebw/c71334dd127d537a15e9d59790f7f5e1
     - https://github.com/pesser/stable-diffusion/commit/bbb52981460707963e2a62160890d7ecbce00e79
     - https://github.com/SHI-Labs/FcF-Inpainting https://praeclarumjj3.github.io/fcf-inpainting/
   - ✅ text based image masking
     - ✅ ClipSeg - https://github.com/timojl/clipseg
     - https://github.com/facebookresearch/detectron2
     - https://x-decoder-vl.github.io/
   - Maskless editing
     - ✅ instruct-pix2pix
     - 
   - Attention Control Methods
     - https://github.com/bloc97/CrossAttentionControl
     - https://github.com/ChenWu98/cycle-diffusion
 - Image Enhancement
   - Photo Restoration - https://github.com/microsoft/Bringing-Old-Photos-Back-to-Life
   - Upscaling
     - ✅ realesrgan 
     - ldm
     - https://github.com/lowfuel/progrock-stable
     - [txt2imghd](https://github.com/jquesnelle/txt2imghd/blob/master/txt2imghd.py)
     - latent scaling + reprocessing
     - stability upscaler
     - rivers have wings upscaler
     - stable super-res?
       - todo: try with 1-0-0-0 mask at full image resolution (rencoding entire image+predicted image at every step)
       - todo: use a gaussian pyramid and only include the "high-detail" level of the pyramid into the next step
       - https://www.reddit.com/r/StableDiffusion/comments/xkjjf9/upscale_to_huge_sizes_and_add_detail_with_sd/
   - ✅ face enhancers
     - ✅ gfpgan - https://github.com/TencentARC/GFPGAN
     - ✅ codeformer - https://github.com/sczhou/CodeFormer
   - ✅ image describe feature - 
     - ✅ https://github.com/salesforce/BLIP
     - 🚫 CLIP brute-force prompt reconstruction
       - The accuracy of this approach is too low for me to include it in imaginAIry
       - https://github.com/rmokady/CLIP_prefix_caption
       - https://github.com/pharmapsychotic/clip-interrogator (blip + clip)
     - https://github.com/KaiyangZhou/CoOp
   - 🚫 CPU support.  While the code does actually work on some CPUs, the generation takes so long that I don't think it's
    worth the effort to support this feature
   - ✅ img2img for plms
   - ✅ img2img for kdiff functions
 - Other
   - Enhancement pipelines
   - text-to-3d https://dreamfusionpaper.github.io/
     - https://shihmengli.github.io/3D-Photo-Inpainting/
     - https://github.com/thygate/stable-diffusion-webui-depthmap-script/discussions/50
     - Depth estimation
       - what is SOTA for monocular depth estimation?
       - https://github.com/compphoto/BoostingMonocularDepth
   - make a video https://github.com/lucidrains/make-a-video-pytorch
   - animations
     - https://github.com/francislabountyjr/stable-diffusion/blob/main/inferencing_notebook.ipynb
     - https://www.youtube.com/watch?v=E7aAFEhdngI
     - https://github.com/pytti-tools/frame-interpolation
   - guided generation 
     - https://colab.research.google.com/drive/1dlgggNa5Mz8sEAGU0wFCHhGLFooW_pf1#scrollTo=UDeXQKbPTdZI
     - https://colab.research.google.com/github/aicrumb/doohickey/blob/main/Doohickey_Diffusion.ipynb#scrollTo=PytCwKXCmPid
     - https://github.com/mlfoundations/open_clip
     - https://github.com/openai/guided-diffusion
   - image variations https://github.com/lstein/stable-diffusion/blob/main/VARIATIONS.md
   - textual inversion 
     - https://www.reddit.com/r/StableDiffusion/comments/xbwb5y/how_to_run_textual_inversion_locally_train_your/
     - https://colab.research.google.com/github/huggingface/notebooks/blob/main/diffusers/sd_textual_inversion_training.ipynb#scrollTo=50JuJUM8EG1h
     - https://colab.research.google.com/github/huggingface/notebooks/blob/main/diffusers/stable_diffusion_textual_inversion_library_navigator.ipynb
     - https://github.com/Jack000/glid-3-xl-stable
   - fix saturation at high CFG https://www.reddit.com/r/StableDiffusion/comments/xalo78/fixing_excessive_contrastsaturation_resulting/
   - https://www.reddit.com/r/StableDiffusion/comments/xbrrgt/a_rundown_of_twenty_new_methodsoptions_added_to/
   - ✅ deploy to pypi
   - find similar images https://knn5.laion.ai/?back=https%3A%2F%2Fknn5.laion.ai%2F&index=laion5B&useMclip=false
   - https://github.com/vicgalle/stable-diffusion-aesthetic-gradients
 - Training
   - Finetuning "dreambooth" style
   - [Textual Inversion](https://arxiv.org/abs/2208.01618)
     - [Fast Textual Inversion](https://github.com/peterwilli/sd-leap-booster) 
   - [Low-rank Adaptation for Fast Text-to-Image Diffusion Fine-tuning (LORA)](https://github.com/cloneofsimo/lora)
     - https://huggingface.co/spaces/lora-library/Low-rank-Adaptation 
   - Performance Improvements
    - [ColoassalAI](https://github.com/hpcaitech/ColossalAI/tree/main/examples/images/diffusion) - almost got it working but it's not easy enough to install to merit inclusion in imaginairy. We should check back in on this.
    - Xformers
    - Deepspeed
    - 