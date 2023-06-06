# controlnet-face

```bash
pip install git+https://github.com/huggingface/diffusers.git transformers accelerate xformers==0.0.16 
pip install bitsandbytes wandb
wandb login



!accelerate launch train_controlnet.py \
 --pretrained_model_name_or_path="stabilityai/stable-diffusion-2-1-base" \
 --output_dir="model_out" \
 --dataset_name=PhilSad/Control-Face-data \
 --conditioning_image_column=conditionning_image \
 --image_column=objective_image \
 --caption_column=caption \
 --resolution=512 \
 --learning_rate=1e-5 \
 --validation_image "./val_images/1.jpg" "./val_images/2.jpg" "./val_images/1.jpg" "./val_images/2.jpg" \
 --validation_prompt "Picture of a man" "Picture of a woman" "High-quality close-up dslr photo of man wearing a hat with trees in the background" "Girl smiling, professional dslr photograph, dark background, studio lights, high quality" \
 --num_train_epochs=3 \
 --tracker_project_name="controlnet-face" \
 --enable_xformers_memory_efficient_attention \
 --checkpointing_steps=5000 \
 --validation_steps=5000 \
 --report_to wandb \
 --push_to_hub
 --train_batch_size=1 \
 --gradient_accumulation_steps=4 \
 --gradient_checkpointing \
 --use_8bit_adam

```