# Gene discovery from biomedical literature
Project to extract in an automatic way gene names from abstracts.

## Research Gruop
**Main researcher**  
Méndez Cruz Carlos Francisco  
**Members**  
Meza Landeros Kevin Emmanuel  
Camacho Hernández Diego Arturo  
Nieto Caballer Victor Eduardo  
Gonzalez Kise Jsé Kenyi  

## Metodology
**Curation**  
Original abstracts were curated and tagged with xml for the identification of the words of interest, genes in this case. 
**CoreNLP**  
The complete dataset was in the same way preprocessed with CoreNLP for its tokenization, lemmatization and part of speech tagging; the target clases of the model: “gene”(G) or “other(O)” were also added.   
**Machine Learning: CRF**  
Being this an supervised learning approach, the complete dataset was splitted in two sets, the training and the testing set, then the training dataset was splitted again, but in a cumulatively way, to see the performance of the model when changing the amount of training data. As shown in the article, a partition 70-30 and non-redundant data sets yields a greater score. 
The program trains a CRF model, specifically a Sklearn one, and proceeds to evaluate it in a different dataset, to see if the rules it learned can be useful to identify genes. In this version of the script, the model is trained using Cross Validation (CV) procedure with number cv and number of iteration (n_iter) both adjustable. Within each CV iteration the hyper parameters are randomly adjusted, with a base parameter. Originally just L1 and L2  were used, but every hyperparameter supported by lbfgs model by Sklearn  is suitable for hyperparameter tuning. 


## Prerequisites
### Programming languages
   - Python (version 2.7, version 3.7)

## Folder content
**CRF**

## Script excecution
The script used along this proyect is: _training_validation_v3.py_ and has the following input parameters:  
--inputPath=PATH    Path of training and test data set  
--trainingFile      File with training data set  
--testFile          File with test data set  
--outputPath=PATH   Output path to place output files  
--excludeStopWords  Filtering stop words (most common words in English, Default = False)  
--excludeSymbols    Filtering punctuation marks (Default = True)  
### Running Example:
python3.4 training_validation_v3.py --inputPath /export/storage/users/kevinml/Bioinfo/Gene-discovery-from-biomedical-literature/data-sets/ --trainingFile training-data-set-70.txt --testFile test-data-set-30.txt --outputPath /export/storage/users/kevinml/Bioinfo/Gene-discovery-from-biomedical-literature/



## Doubts
For information regarding scripts and data sets used in the article, please read README carefully. If the doubts persist, feel freely to contact us: dcamacho@lcg.unam.mx.
