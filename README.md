# ner-dataset-modified-dee
<b>A set of Dataset to build the Indonesian NER</b>
<br>
<i>(Dataset untuk Membangun Named Entity Recognizer (NER) untuk Bahasa Indonesia)</i> <br>

The dataset conforms with dataset format of Stanford-NER (https://nlp.stanford.edu/software/CRF-NER.shtml) <br>
The dataset may be used for free, but if you want to publish paper/publication using the dataset, please cite this publication: <br>

<b>Ika Alfina, Septiviana Savitri, and Mohamad Ivan Fanany, <i>"Modified DBpedia Entities Expansion for Tagging Automatically NER Dataset"</i>, in Proceeding of International Conference on Advanced Computer Science and Information Systems (ICACSIS) 2017 in Bali, Indonesia (accepted).</b>

<br>We provide three versions of NER dataset as we explained on the paper:
1. dataset created using original DEE method, file name: 20k-dee.txt, with properties file: 20k-dee.prop
2. dataset created using Modified DEE (our project), file name: 20k-mdee.txt, with properties file: 20k-mdee.prop
3. dataset created using Modified DEE plus gazettes (our project), file name: 20k-mdee-gazz.txt, with properties file: 20k-mdee-gazz.prop
<br>

<b>How to create NER model using the dataset?</b><br>

You can use many methods to create NER model. One of them is using Stanford NER library.<br>
The steps to create NER model using Stanford NER library are as follows:
1. Download Stanford NER (https://nlp.stanford.edu/software/CRF-NER.shtml)
2. Download the dataset and its properties file (file with .prop extension)
3. Use Stanford NER classifier to create the model. <br>
   For example: <br>
      java -cp stanford-ner.jar edu.stanford.nlp.ie.crf.CRFClassifier -prop 20k-mdee.prop <br>
      
      I recommend to increase heap size so you can train the dataset on computer with limited RAM:<br>
      
      java -Xmx1024m-cp stanford-ner.jar edu.stanford.nlp.ie.crf.CRFClassifier -prop 20k-mdee.prop <br>

   Let say this step will create a NER model file named "idner-model-15000-mdee.ser.gz"
 
4. Create or use a testing dataset, lets say the file name is "testing.txt"
5. Evaluate the NER model using Stanford NER library <br>
   For example:<br>
        java -cp stanford-ner.jar edu.stanford.nlp.ie.crf.CRFClassifier -loadClassifier idner-model-20k-mdee.ser.gz -testFile testing.txt 
   

