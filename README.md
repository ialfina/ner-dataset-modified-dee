# ner-dataset-modified-dee
<b>Modified DBpedia Entities Expansion for Tagging Automatically NER Dataset</b>

The objective of the project: to create NER dataset that automatically labeled
The dataset can be used to create NER for Indonesian language

<b>Dataset</b><br>
The dataset conforms with dataset format of Stanford-NER (https://nlp.stanford.edu/software/CRF-NER.shtml)

The dataset is available for personal use, but if you want to publish paper using the dataset you should cite this publication:

Ika Alfina, Septiviana Savitri, and Mohamad Ivan Fanany, <i>"Modified DBpedia Entities Expansion for Tagging Automatically NER Dataset"</i>, in Proceeding of International Conference on Advanced Computer Science and Information Systems (ICACSIS) 2017 in Bali, Indonesia (accepted).

<b>How to create model using the dataset?</b><br>

We provide three version of dataset as we explain on the paper:
1. dataset created using original DEE method
2. dataset created using Modified DEE (our project)
3. dataset created using Modified DEE plus gazettes (our project)

If you want to create model using these dataset, you should follow these step:
1. Download Stanford NER (https://nlp.stanford.edu/software/CRF-NER.shtml)
2. Download the dataset and its properties file (file with .prop extension)
3. Use Stanford NER classifier to create the model. <br>
   For example: <br>
      java -cp stanford-ner.jar edu.stanford.nlp.ie.crf.CRFClassifier -prop 15000-mdee.prop 
    
   Let say this step will create a NER model file named "idner-model-15000-mdee.ser.gz"
 
4. Create or use a testing dataset, lets say the file name is "testing.txt"
5. Evaluate the NER model using Stanford NER library <br>
   For example:<br>
        java -cp stanford-ner.jar edu.stanford.nlp.ie.crf.CRFClassifier -loadClassifier idner-model-15000-mdee.ser.gz -testFile testing.txt 
   

