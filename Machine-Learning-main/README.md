## Machine-Learning
### Debate artigo 
**"Text Classification in Legal Documents Extracted from Lawsuits in Brazilian Courts"**

O artigo debate a classificação de acordo com a classe processual, nosso intuito é verificar a classe de direito material. A materia tem o assunto.

**Número do precedente judicial** que ele está citando tambem seria um otimo atributo para classificar a materia

Nosso problema é **multi-label classification**

o **NER (Named Entity Recognizer)** é utilizado para identificar a leis e decretos no texto, logo após faz uma validação com o banco de dados **LENER-BR**.

Saber o artigo da lei é interessante para conseguimos identificar a materia do assunto. No paper demonstrou que eles so precisaram verificar a lei e não o artigo.

BERT model get the best result for they problem. Bertimbau is a repository who contains pre-trainer BERT models trained on the portuguese language.

Ele utilizada varios embeddings:

+  Cenario 1: Todos documentos de um processo 
+ Cenario 2: Concatenação de todos documentos que tenha pelo menos uma legislação
+ Cenario 3: Concatenação da legislação citada
+ Cenario 4: Concatenação de todos documentos que citam uma legislação, juntamente com o resumo da legislação
+ Cenario 5: Juntou o cenario 2 e 5
+ Cenario 6: Transformação TF-IDF
+ Cenario 7: Cenario 2 com o 6
+ Cenario 8: Cenario 3 com o 6
+ Cenario 9: Cenario 4 com 6
+ Cenario 10: Cenario 2 com o  
+ Cenario 3 , o resumo da legislação, e o cenario 6
+ Cenario 11:

Os modelos utilizados

+ **Random Forest**
+ **SVM**
+ **XGBoost**
+ **BERT(BERTimbau)**

A melhor perfomance, com 0.88, foi alcançada pelo **BERTimbau**

####  VERIFICAR ARTIGO:
 **"BERTimbau: pretrained BERT models for Brazilian Portuguese."**

### Pesquisar algo mais simples para fazer a verificação a partir do texto da materia


### Multi-Class
| X | Class |
|--- |--- |
| X1 | Positive | 
| X2 | Negative |
| X3 | Neutral | 

### Multi-Label
| X | Class 1 | Class 2 | Class 3|
|--- |--- |--- |--- |
| x1 | 0 | 0 | 0 |
| x2 | 0 | 0 | 1 |
| x3 | 1 | 0 | 1 |

Adapted algoritms (KNM, RF, etc)

## MultiLabel text classification
### Binary relevance
Dividira o problema em varios multi-classes

### Classifier Chains
Manterá a relação de correlação de cada caso, criando features
Exemplo: 

| X | Class 1 | Class 2 | Class 3|
|--- |--- |--- |--- |
| x1 | 0 | 0 | 0 |
| x2 | 0 | 0 | 1 |
| x3 | 1 | 0 | 1 |

O primeiro caso (y1):
| X | Class |
|--- |--- |
| X1 | 0 | 
| X2 | 0 |
| X3 | 0 | 

Segundo caso (y2):
| X | y1 | Class|
|--- |--- |--- |
| X1 | 0 | 0 |
| X2 | 0 | 0 | 
| X3 | 0 | 1 |

Caso final:

| X | y1 |  y2 | Class|
|--- |--- |--- |--- |
| X1 | 0 | 0 | 1 |
| X2 | 0 | 0 | 0 |
| X3 | 0 | 1 | 1 |

### Powerset
Transformará o problema em um Multi-Class e ira retornar uma classe para cara combinação de label no nosso dataset
O primeiro caso (y1):
| X | Class |
|--- |--- |
| X1 | 1 | 
| X2 | 2 |
| X3 | 3 | 