This folder contains the revised three NER datasets in the main folder.
Why they need revision? We forgot to insert "blank line" between sentences.

Since we couldn't find the original sentences before tokenization was applied on, we wrote a script that separated the dataset using the "." token as the delimiter. As the result, this script separated each of three datasets into 2,240 sentences. Note, that we used PTBTokenizer from Stanford CoreNLP to split the original files of 20,000 sentences. There must be some error in tokenizing Indonesian sentences. Anyone want to build a better tokenizer for Indonesian? ;-) 
