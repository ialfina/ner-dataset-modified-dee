This folder contains the revised three NER datasets of 20k sentences in the main folder.
Why do they need revision? We forgot to insert "blank line" between sentences. 

Since we couldn't find the original file of 20,000 sentences before tokenization was applied on, we wrote a script that separated the dataset using the "." token as the delimiter. As the result, this script separated each of three datasets into 20,240 sentences. 

Note that we used PTBTokenizer from Stanford CoreNLP to split the original file. There must be some errors in tokenizing the original file, since it should be 20,000 not 20,240 sentences. 

Does anyone want to build a better tokenizer for Indonesian? ;-) 
