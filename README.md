# CS-6784-2 HW 1

## 3.2.1 Total params
Total parameters in CLIP is 149620737

## 3.2.2 Outputs
<img width="1552" height="672" alt="Screenshot from 2025-09-04 02-07-15" src="https://github.com/user-attachments/assets/dc176c4a-2f30-4a44-8d65-1cda1cba4e21" />

## 3.2.3 Model Deisgn
The model architecture design I had for this part is as follows:
a) Frozen CLIP Image Encoder:
Uses the pre-trained openai/clip-vit-base-patch16 model
Total CLIP parameters: 149,620,737 (all frozen)
Processes input images and outputs 512-dimensional embeddings

b) Two-Layer Classifier Network:
- Layer 1: Linear layer (512 → 256) followed by ReLU activation
- Layer 2: Linear layer (256 → 10) for final classification (digits 0-9)
Trainable parameters: 133,898

After playing around with a couple of learning rates, lr=0.001 had the best performance abiet a bit slow and I chose to use CrossEntropyLoss for my loss function as it's specifically designed for multi-class classification where each sample belongs to exactly one class.

From the training output visible in the notebook:
Based on completed epochs (through epoch 3-4):
Training Accuracy: ~66.31% (epoch 4, trending upward)
Test Accuracy: ~70.24% (epoch 3, last complete result shown)
The training shows a consistent upward trend:
Epoch 1: Train 56.27%, Test 67.44%
Epoch 2: Train 62.86%, Test 67.10%
Epoch 3: Train 64.92%, Test 70.24%
Epoch 4: Train 66.31%, Test 69.70%
Epoch 5: Train 67.51%, Test 71.50%

**Note**: marginal benefit with increasing epochs to i.e. 12
<img width="813" height="521" alt="image" src="https://github.com/user-attachments/assets/5727fad7-d2a6-4547-af31-e344748ff035" />



Observation: 

### 3.2.4 Set up
To replicate my conda environment, please run "pip install -r requirements.txt" in the terminal after cloning this repo and cd-ing into the working directory. 

