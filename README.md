# Gene discovery from biomedical literature
Project to create a bioinformatic approach for the extraction of human gene names within biomedical abstracts, making use of a supervised Machine Learning model: Conditional Random Fields (CRFs).

## Research Group
**Main researcher**  
Méndez Cruz Carlos Francisco  
**Members**  
Meza Landeros Kevin Emmanuel  
Camacho Hernández Diego Arturo  
Nieto Caballero Victor Eduardo  
González Kise José Kenyi  

## Metodology
**Curation**  
Original abstracts were curated and tagged with xml for the identification of the words of interest, genes in this case. 
**CoreNLP**  
The complete dataset was in the same way preprocessed with CoreNLP for its tokenization, lemmatization and part of speech tagging; the target clases of the model: “gene”(G) or “other(O)” were also added.   
**Machine Learning: CRF**  
Being this an supervised learning approach, the complete dataset was splitted in two sets, the training and the testing set, then the training dataset was splitted again, but in a cumulatively way, to see the performance of the model when changing the amount of training data. As shown in the article, a partition 70-30 and non-redundant data sets yields a greater score. 
The program trains a CRF model, specifically a Sklearn one, and proceeds to evaluate it in a different dataset, to see if the rules it learned can be useful to identify genes. In this version of the script, the model is trained using Cross Validation (CV) procedure with number cv and number of iteration (n_iter) both adjustable. Within each CV iteration the hyper parameters are randomly adjusted, with a base parameter. Originally just L1 and L2  were used, but every hyperparameter supported by lbfgs model by Sklearn  is suitable for hyperparameter tuning. 

The program trains a CRF model, specifically a Sklearn one, and proceeds to evaluate it in a different dataset, to see if the rules it learned can be useful to identify genes. In this version of the script, the model is trained using Cross Validation (CV) procedure with number cv and number of iteration (n_iter) both adjustable. Within each CV iteration the hyper parameters are randomly adjusted, with a base parameter. Originally just L1 and L2  were used, but every hyperparameter supported by lbfgs model by Sklearn  is suitable for hyperparameter tuning. 

## Prerequisites
### Programming languages
   - Python (version 2.7, version 3.7)

## Folder content
- **data-sets**  
A directory that has all of the data sets used in the course of this article. Also contains the splitted data sets, from which we modeled the growing of the score with the bigger the training sets were. 
-   genes.txt 	
-	test-data-set-30.txt 	
-	text-annotated-abstracts.txt 	
-	training-data-set-10.txt
-	training-data-set-20.txt 	
-	training-data-set-30.txt 
-	training-data-set-35.txt 
-	training-data-set-40.txt 	
-	training-data-set-50.txt 	
-	training-data-set-60.txt 	
-	training-data-set-70.txt

- **models**  
An obligatory directory. It guards the best model obtained by our team. It also serves to keep an update from new models trained.  

- **reports**  
An obligatory directory, needed to report the yield of the trained CRF. In this directory resides all of the results of training with increasing training set.  

- Gene_extraction_from_Biomedical_Literature.pdf :  Article in pdf format.
- training_validation_v3.py: the original script for training an testing  a lbfgs CRF model

## Run the Programm
### Cloning the repositoty
In a unix system perform a git clone, in order to have local access to the multiple data sets and directories needed for the outphase.   
> git clone https://github.com/kevinLCG/Gene-discovery-from-biomedical-literature
### Script excecution
The script used along this proyect is: _training_validation_v3.py_ and has the following input parameters:  
--inputPath=PATH    Path of training and test data set  
--trainingFile      File with training data set  
--testFile          File with test data set  
--outputPath=PATH   Output path to place output files  
--excludeStopWords  Filtering stop words (most common words in English, Default = False)  
--excludeSymbols    Filtering punctuation marks (Default = True)  
### Running Example
python3.4 training_validation_v3.py --inputPath /export/storage/users/kevinml/Bioinfo/Gene-discovery-from-biomedical-literature/data-sets/ --trainingFile training-data-set-70.txt --testFile test-data-set-30.txt --outputPath /export/storage/users/kevinml/Bioinfo/Gene-discovery-from-biomedical-literature/
### Output Format Example
report_training-data-set-<A special notation of the training data set>.fStopWords_False.fSymbols_True.txt



## Doubts
For information regarding scripts and data sets used in the article, please read README carefully. If the doubts persist, feel freely to contact us: dcamacho@lcg.unam.mx.
