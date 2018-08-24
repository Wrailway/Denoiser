# Denoiser
Android app for demonstrating the speech enhancing capabilities of the Deep Denoising AutoEncoder (DDAE) that is capable of audio recording, playback and de-noising with a pre-trained DNN model. 


Target SDK 26


Requires permissions Write to External Storage and Record Audio


# Freezing trained models
To export pre-trained models into a format the application can use, we must "freeze" the model into a protobuf file. Do this by using the python script provided called "freeze.py". Make sure you have the save files from the Tensorflow Saver of your training session. At the bottom of freeze.py, configure the variable "model_dir" to the file path of your save files and the variable "output_nodes_names" into the output node of your model. For example, if you are using DDAE, the output node name would be "REG_Net/DNN/Add_4". Now you may run the script and a protobuf file will be generated in the location of "model_dir" called "frozen_model.pb". You may rename this to whatever you like. Next, place this protobuf file in the assets folder of the application located at app/src/main/assets/. In order for the application to find it during runtime, edit the variable "modelName" at the top of MainActivity.java to whatever you named yout frozen model. The TensorflowInferenceInterface will now be able to find and use the frozen model.
