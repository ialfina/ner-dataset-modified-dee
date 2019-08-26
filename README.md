# Datasets for Building the Indonesian NER

<b>(Dataset untuk Membangun Named Entity Recognizer (NER) untuk Bahasa Indonesia)</b> <br>

This repository contains resources of a project named Modified DBpedia Entities Expansion (MDEE) (Alfina, et al., 2017). We share:
- Three NER datasets used in the experiments explained in the paper (in the main folder), each consists of 20,000 sentences, along with the gold standard.
- Three NER datasets, as the revised version of the three NER datasets in the main folder (in the revised-20k folder).
- The original names in Indonesian DBpedia (in "original-dbpedia" folder).
- Two versions of DBpedia explained in the paper (in "expanded-dbpedia" folder): MDEE, and MDEE_Gazetteer
- A dataset of 48,957 sentences named SINGGALANG (in "singgalang" folder). We used expanded DBpedia of MDEE_Gazetteer to label this dataset. 

<b> The NER Datasets</b><br>
The datasets conforms with the dataset format of <a href="https://nlp.stanford.edu/software/CRF-NER.shtml">Stanford-NER</a> <br>
Four named entity classes are used:
- "Person" for person names
- "Place" for place names
- "Organisation" for organization names
- "O" for others

<br>List of dataset in main folder:
<br>1. dataset created using original DEE (Alfina et al., 2016), file name: 20k-dee.txt, with properties file: 20k-dee.prop
<br>2. dataset created using Modified DEE (Alfina et al., 2017), file name: 20k-mdee.txt, with properties file: 20k-mdee.prop
<br>3. dataset created using Modified DEE plus gazetteer (Alfina et al., 2017), file name: 20k-mdee-gazz.txt, with properties file: 20k-mdee-gazz.prop
<br>4. A gold standard created by Luthfi, et al (2014)
<br>
Each version of NER datasets consist of 20,000 sentences from Wikipedia articles in the Indonesian language that were labeled automatically. <br>
<br>

<b> The SINGGALANG dataset</b><br>
We provide a new NER dataset in this repository, named SINGGALANG. The specifications of this dataset are:
- The number of sentences: 48,957 
- Generated using expanded DBpedia of MDEE_Gazett (the best version of those three expanded DBpedia)

<b> How to cite these works</b><br>
The dataset may be used for free, but if you want to publish paper/publication using the dataset, please cite these publications: <br>

- The DEE corpus: 

<a href="https://www.researchgate.net/publication/308788318_DBpedia_Entities_Expansion_in_Automatically_Building_Dataset_for_Indonesian_NER">Ika Alfina, Ruli Manurung, and Mohamad Ivan Fanany, <i>"DBpedia Entities Expansion in Automatically Building Dataset for Indonesian NER"</i>, in Proceeding of 8th International Conference on Advanced Computer Science and Information Systems 2016 (ICACSIS 2016).</a><br>

- The MDEE corpus:

<a href="https://www.researchgate.net/publication/320131070_Modified_DBpedia_Entities_Expansion_for_Tagging_Automatically_NER_Dataset">Ika Alfina, Septiviana Savitri, and Mohamad Ivan Fanany, <i>"Modified DBpedia Entities Expansion for Tagging Automatically NER Dataset"</i>, in Proceeding of 9th International Conference on Advanced Computer Science and Information Systems 2017 (ICACSIS 2017).</a><br>

- The Gold Standard

<a href="https://www.researchgate.net/publication/286428192_Building_an_Indonesian_named_entity_recognizer_using_Wikipedia_and_DBPedia">Andry Luthfi, Bayu Distiawan, and Ruli Manurung, <i>"Building an Indonesian named entity recognizer using Wikipedia and DBPedia"</i>, in the Proceesing of 2014 International Conference on Asian Language Processing (IALP)</a>
<br>

<b>How to create NER model using the dataset?</b><br>

We suggest you to use the Stanford NER library.<br>
The steps to create NER model using Stanford NER library are as follows:
1. Download <a href="https://nlp.stanford.edu/software/CRF-NER.shtml">Stanford NER</a>
2. Download the dataset and its properties file (file with .prop extension)
3. Use Stanford NER classifier to create the model. <br>
   For example: <br>
      java -cp stanford-ner.jar edu.stanford.nlp.ie.crf.CRFClassifier -prop 20k-mdee.prop <br>
      
      I recommend to increase the heap size so you can train the dataset on computer with limited RAM. Add option like "-Xmx1024m" on the command, for example:<br>
      
      java -Xmx1024m -cp stanford-ner.jar edu.stanford.nlp.ie.crf.CRFClassifier -prop 20k-mdee.prop <br>
      
      if this still doesn't work, increase the number. For example: "-Xmx8000m". This works for me :)

   Let say this step will create a NER model file named "idner-model-20k-mdee.ser.gz"
 
4. Create or use a testing dataset. Lets say the file name is "testing.txt"
5. Evaluate the NER model using Stanford NER library <br>
   For example:<br>
        java -cp stanford-ner.jar edu.stanford.nlp.ie.crf.CRFClassifier -loadClassifier idner-model-20k-mdee.ser.gz -testFile testing.txt 
   

