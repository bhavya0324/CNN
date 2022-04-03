# CS6910_Assignment_2

<strong> Dataset : </strong> iNaturalist Dataset </br>

<strong> How to download dataset </strong> : </br> 

The dataset is collected using wget and for unzipping we used following commands : <br/>
```
!wget https://storage.googleapis.com/wandb_datasets/nature_12K.zip 

!unzip 'nature_12K.zip'
```
This wont take much time just a few seconds to download and unzip. </br>

This Repository has 3 ipynb files : <br/>

<strong> For Part A </strong> : Final_Part_A_Command_Line.ipynb and Part_A.ipynb <br/>
<br/>
<strong> For Part B </strong> : Part_B_final.ipynb <br/>
<br/>
<br/>
<strong> Steps to Execute for Part A : </strong> <br/>
<br/>
<br/>
<strong> If you want to run Part A using Sweep Configuration then open Part_A.ipynb file using the link to colab option and do the following </strong> : <br/>

1.) We have given 20 epochs if you want to change the number of epochs then go to train function and change epochs. <br/>

2.) There will be two blocks Actual sweep configuration (which we used to find best model) and Best model sweep configuration (Which we got as best configuration) <br/>

If you want to run for all sweeps then remove comments in actual sweep configuration block for sweep configuration and comment the best model sweep. <br/>

If you want to run the best sweep then run as it is without any changes.<br/>

If you want to add any parameters such as filter_size,pool_size, data_augmentation etc.., then go to sweep configuration and add or modify accordingly . <br/>

Now Run the cells from top to bottom <br/>

<strong> If you want to run Part A using Command line arguments then open Final_Part_A_Command_Line.ipynb and execute as follows : </strong> <br/>

1.) Change the number of epochs in main function as you want. <br/>

Now Run the cells from top to bottom <br/>

2.)Input the Following values in run time , as following example input : <br/>

```
enter "Yes" if you want data to be augmented else enter "No": Yes
enter batch size:128
enter number of layers: 5
enter number of filters: 64
enter size of filters: 3
enter pool size: 2
enter filter_organization:1
enter no of neurons in dense layer: 128
enter "Yes" if you want batch normalization else enter "No": Yes
enter value of dropout: 0.2
```
<br/>
<br/>
<br/>
<strong> Steps to Execute for Part B : </strong> <br/>
<br/>
<br/>
1.) We have given 5 as epochs, if you want to change the number of epochs then go to train function and change the following : <br/>

```
model.fit(train_data,
                    steps_per_epoch = ceil((float) (train_data.n) / train_data.batch_size),
                    epochs = input your epochs,
                    callbacks = [WandbCallback()],
                    validation_data = val_data,
                    validation_steps = ceil((float) (val_data.n) / val_data.batch_size)
                    )
```
<br/>
2.) If you want add a new pre trained model then do the steps as follows : <br/>
step:1 (In helper function add the following line ) <br/>

```
if model == "new_model":
   return new_model(input_shape = (H , W , D), weights = "imagenet", include_top = False)
```
<br/>
step:2 (In train function add the following lines) <br/>

```
if(config.model == "my_model"):
      l2_conv_layers = [first_last_conv_layer_number_of_new_model, second_last_conv_layer_number_of_new_model]
```
<br/>
3.) If you want to change the number of trainable layers then add the number in sweep configuration for set_conv_layers.



