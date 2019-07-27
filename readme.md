# CONTEXTUAL ENTITY DISAMBIGUATION (K-CAP-2019)


## Evaluation Sheets

The evaluation sheets are **considered the gold standards** and are in a user friendly test format. They contain the experts validation as well as the machines' ones. The evaluation sheet presents the experts validations and the automatic validations. It is also filled with some additional necessary data to help the expert disambiguate the resource. These include information such as name, husband, wife and kid's names if any, marriage, baptism or burial dates, etc.   In these files, the experts annotated a **GOOD** cluster as "**G**" otherwise "**B**". Four evaluation sheets exist: 

+ No cycle: clusters for which no cycle is observed.
+ Cycle: clusters for which a cycle is observed.
+ Reconciled: clusters that have been reconciled based on the presence of one or more cycles.
+ Removed grey: clusters for which the automated evaluation is not in the interval [0.8, 0.9[  (grey area). 

```
---------------------------------
---- EVALUATION SHEET EXAMPLE ---
---------------------------------
									

COUNT  CLUSTER-ID             CLUSTER-SIZE  |MACHINE-EVAL           |MACHINE-MIN-EVAL       |MACHINE-AVG-EVAL       |MACHINE-ALL-EVAL       |HUMAN-EVAL  |HAS-CYCLE   NOT GOOD  CYCLE  |COMMENT                |RESOURCES              
1      N7395160203604709397   3             |-GOOD [1.0]-           |-GOOD [1.0]-           |-GOOD [1.0]-           |-GOOD [1.0]-           |-G-         |yes                          |                       |RESOURCE                            | DATASET                             | FULL_NAME                           | MARRIAGE                            | HUSBAND                             | WIFE                                | PREVIOUSHUSBAND                     | PREVIOUSWIFE                        | ONES_DEATH                          | FIRST                               | SECOND                              | DEATH                               | BIRTH                               | KIDS_BAPTISM
                                            |                       |                       |                       |                       |            |            -1-       -X-    |                       |saaId24692118p2                     | Baptism002                          | Amerongen, Jan [van]                |                                     | Amerongen, Jan [van]                | Roijen, Giertje [van]               |                                     |                                     |                                     |                                     |                                     |                                     |                                     | 1624-12-23
                                            |                       |                       |                       |                       |            |            -1-       -X-    |                       |saaId24725121p2                     | Baptism002                          | Amerongen, Jan [van]                |                                     | Amerongen, Jan [van]                | Roijen, Geertje [van]               |                                     |                                     |                                     |                                     |                                     |                                     |                                     | 1630-06-23
                                            |                       |                       |                       |                       |            |            -1-       -X-    |                       |555                                 | Ecartico                            | Amerongen, Jan [van]                | 1620-06-13                          | Amerongen, Jan [van]                | Roijen, Geertje [van]               |                                     |                                     |                                     |                                     |                                     |                                     | 1591-01-01                          |

2      N6025972999207757492   2             |-BAD [0.667]-          |-BAD [0.667]-          |-BAD [0.667]-          |-BAD [0.667]-          |-G-         |yes                          |                       |RESOURCE                            | DATASET                             | FULL_NAME                           | MARRIAGE                            | HUSBAND                             | WIFE                                | PREVIOUSHUSBAND                     | PREVIOUSWIFE                        | ONES_DEATH                          | FIRST                               | SECOND                              | DEATH                               | BIRTH                               | KIDS_BAPTISM
                                            |                       |                       |                       |                       |            |            -1-       -X-    |                       |13377                               | Ecartico                            | Goddeling, Thomas Jacobsz           | 1639-03-05                          | Goddeling, Thomas Jacobsz           | Cornelis, Apolonia                  |                                     |                                     |                                     |                                     |                                     |                                     |                                     |
                                            |                       |                       |                       |                       |            |            -1-       -X-    |                       |saaId26346222p1                     | Marriage003                         | Goddeling, Thomas Jacobsz           | 1639-03-05                          | Goddeling, Thomas Jacobsz           | Cornelis, Apolonia                  |                                     |                                     |                                     |                                     |                                     |                                     |                                     |

3      N8168393585806295922   10            |-ACCEPTABLE [0.848]-   |-BAD [0.774]-          |-BAD [0.814]-          |-BAD [0.829]-          |-G-         |yes                          |                       |RESOURCE                            | DATASET                             | FULL_NAME                           | MARRIAGE                            | HUSBAND                             | WIFE                                | PREVIOUSHUSBAND                     | PREVIOUSWIFE                        | ONES_DEATH                          | FIRST                               | SECOND                              | DEATH                               | BIRTH                               | KIDS_BAPTISM

```

## Ground-truth

The ground-truth data (```gold-cycle-transferred.csv``` and ```gold-no-cycle-transferred.csv```) are .csv files compiled based on the evaluation sheets. It allows a quick overview on how the judge validated each cluster and split those that are not correct.

**Columns Description:**

+ CLUSTER-COUNT	: It tells us how many clusters are generated.
+ STATUS			: The human evaluation of the quality of the cluster. A single wrong node in an identity link cluster triggers an annotation of **B** indicating **BAD** and **G** (**GOOD**) otherwise.
+ CLUSTER-SIZE	: The size of the cluster.
+ DATASET			: The dataset in which the node can be found.
+ RESOURCE-URI	: The local name extract from the resource URI.
+ CLUSTER-ID		: The ID of the cluster.
+ ILN-GROUP		: If an other number except 1 is found, for example 3, it means that the cluster is split into three sub-clusters.

```
--------------------------------------------------
-- THIS IS AN EXAMPLE OF THE GOLD STANDARD FILE --
--------------------------------------------------

CLUSTER-COUNT	STATUS	CLUSTER-SIZE	DATASET	RESOURCE-URI	CLUSTER-ID	ILN-GROUP
						
1	B	7	Baptism002	saaId24273101p1	PH19b7294f077ecf0	1
1	B	7	Baptism002	saaId24444353p1	PH19b7294f077ecf0	2
1	B	7	Baptism002	saaId24515677p1	PH19b7294f077ecf0	1
1	B	7	Baptism002	saaId24544852p1	PH19b7294f077ecf0	1
1	B	7	Baptism002	saaId24547914p1	PH19b7294f077ecf0	1
1	B	7	Baptism002	saaId24621793p1	PH19b7294f077ecf0	2
1	B	7	Ecartico	23023	PH19b7294f077ecf0	1
						
2	G	4	Baptism002	saaId24509717p2	PH32817db85dd091e	1
2	G	4	Baptism002	saaId24524508p2	PH32817db85dd091e	1
2	G	4	Baptism002	saaId24583287p2	PH32817db85dd091e	1
2	G	4	Ecartico	22569	PH32817db85dd091e	1
						
3	G	6	Baptism002	saaId24548746p2	PH2951197d5b19373	1
3	G	6	Baptism002	saaId24565578p2	PH2951197d5b19373	1
3	G	6	Baptism002	saaId24584356p2	PH2951197d5b19373	1
3	G	6	Baptism002	saaId24722679p2	PH2951197d5b19373	1
3	G	6	Ecartico	6213	PH2951197d5b19373	1
3	G	6	Marriage003	saaId26386917p1	PH2951197d5b19373	1
						
4	G	7	Baptism002	saaId24331962p2	PH04a1c0123f05b6f	1
4	G	7	Baptism002	saaId24335997p2	PH04a1c0123f05b6f	1
4	G	7	Baptism002	saaId24454450p2	PH04a1c0123f05b6f	1
4	G	7	Baptism002	saaId24609060p2	PH04a1c0123f05b6f	1
4	G	7	Baptism002	saaId24711286p2	PH04a1c0123f05b6f	1
4	G	7	Ecartico	7900	PH04a1c0123f05b6f	1
4	G	7	Marriage003	saaId26400712p1	PH04a1c0123f05b6f	1
```


## Confusion Matrices

These files are composed of confusion matrices (ConfMat) describing the performances of the algorithms.
The ConfMat below is the results for the 642 clusters of size bigger that two that have been reconciled. Here, three files are provided:

+ No cycle
+ Cycle
+ Reconciled 
+ Removed Grey

```
---------------------------------
--- CONFUSION MATRIX EXAMPLE  ---
---------------------------------

                   -----------------------------------
                   |       642 GROUND TRUTHS         |
                   -----------------------------------
                   |  GT Positive   |  GT Negative   |
                   |      353       |      289       |
---------------------------------------------------------------------------------------------------------
        | Positive | True Positive  | False Positive |      Precision      | False discovery rate (FDR) |
        |   472    |      327       |      145       |        0.693        |           0.307            |
PREDICT -------------------------------------------------------------------------------------------------
  642   | Negative | False Negative | True Negative  | False omission rate | Negative predictive value  |
        |   170    |       26       |      144       |        0.153        |           0.847            |
---------------------------------------------------------------------------------------------------------
                   |     Recall     |    Fall-out    | P. Likelihood Ratio |   F1 score     Accuracy    |
                   |     0.926      |     0.502      |        1.38         |     0.793        0.734     |
                   --------------------------------------------------------------------------------------
```

## Data

+ **Linkset**: a .csv file in the format: subject, object, strength (s,o,v)

	**Link Discovery.** The SAA datasets are matched against Ecartico with a 0.85 threshold for approximate string matching on names to unveil potential notable mentioned. These notable mentions from Marriage, Baptism and Burial are then matched against each other within and across datasets using the same similarity threshold. Overall we end up with about 120K links.
	
+ **Associations:** a .csv file in the format subject, object (s,o)

	The association extracted from the SAA datasets are based on marriage events thereby creating 3970 pairwise associations.
	
+ ILNs: Four files are available. Two files are about the original ILNs (Custers and Root) and two other files are about the reconciled ILNs (Custers-reconciled and Root-reconciled).

	**Mappings:** The files ```ilns_map.txt.gz``` and ```ilns_reconciled_map.txt.gz``` are python serialised dictionary objects mapping each resource URI to the cluster it belongs too. 

	**Clusters:** The files ```ilns.txt.gz``` and ```ilns_reconciled.txt.gz``` are serialised python dictionary objects modelled as described below.


```
-----------------------------------------------------------------------------
-- EXAMPLE OF WHAT WE GET AS CLUSTER FROM THE SERIALISED PYTHON DICTIONARY --
-----------------------------------------------------------------------------
{
    P1832892825: 
    {
        'nodes': set(['<http://www.grid.ac/institutes/grid.449957.2>',
                    '<http://risis.eu/eter_2014/resource/NL0028>']),
	
        'strengths': {key_H57f2f44c3fd2ece: ['1', '1']},
	
        'links': set([('<http://risis.eu/eter_2014/resource/NL0028>',
                 '<http://www.grid.ac/institutes/grid.449957.2>')])}
	},
	...
}
```
The **key_H57f2f44c3fd2ece** can be obtained with the function `get_key(node_1, node_2)`

```
for example: get_key('<http://www.grid.ac/institutes/grid.449957.2>','<http://risis.eu/eter_2014/resource/NL0028>')
The function is described below.
```
	
```
---------------------------------
-- GET KEY FUNCTION DEFINITION --
---------------------------------

	def getkey(node_1, node_2):

	    from hashlib import md5
	    def hashe_it(obj):
	        h = md5()
	        h.update(bytes(obj.__str__(), encoding='utf-8'))
	        return F"H{h.hexdigest()[:15]}"
	
	    return "key_{}".format(str(hashe_it((node_1, node_2))).replace("-", "N")) \
			if node_1 < node_2 \
			else "key_{}".format(str(hashe_it((node_2, node_1))).replace("-", "N"))
	
```

	
	
	
	