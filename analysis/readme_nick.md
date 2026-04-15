i trained two different models:
- one was trained from scratch
- other was pretrained on imagenet and then was fine tuned on dataset

I used the same training hyperparmas for both models


`/home/log/Github/yolo_data_mining_project/analysis/training_analysis_scratch_pretrain.ipynb`
this notebook shows the predictions and training details for the from scratch model. It also has all the comparisons to the finetuned model with inference speed and efficiency.

for the inference metrics, both models should be basically the same. iwould recommend you just list out the numbers for that section and don't use the plots comparing them. The only reason they look different is because of measurement noise


`/home/log/Github/yolo_data_mining_project/analysis/training_analysis_imagenet_finetune.ipynb`
this notebook contains all the details for the finetuned model


`/home/log/Github/yolo_data_mining_project/analysis/runs`
I also copied over the training directory over here with the large files removed. there's some interesting files to look at in here. Run 7 is the scratch model. Run 10 is the finetuned model. You should talk about some of the important hyperparams in there.

