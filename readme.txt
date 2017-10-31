I. Background and Goals of Project
  Sentiment analysis is increasingly viewed as a vital task both from an academic and a commercial standpoint. The majority of current approaches, however, attempt to detect the overall polarity of a sentence, paragraph, or text span, regardless of the entities mentioned (e.g., laptops, restaurants) and their aspects (e.g., battery, screen; food, service).
  By contrast, this task is concerned with aspect based sentiment analysis (ABSA), where the goal is to identify the aspects of given target entities and the sentiment expressed towards each aspect. Datasets consisting of customer reviews with human- authored annotations identifying the mentioned aspects of the target entities and the sentiment polarity of each aspect will be provided.


II. Description of Subtasks
  <II-1>Subtask 1: Aspect term extraction
  Given a set of sentences with pre-identified entities (e.g., restaurants), identify the aspect terms present in the sentence and return a list containing all the distinct aspect terms. An aspect term names a particular aspect of the target entity.
  For example, "I liked the service and the staff, but not the food”, “The food was nothing much, but I loved the staff”. Multi-word aspect terms (e.g., “hard disk”) should be treated as single terms (e.g., in “The hard disk is very noisy” the only aspect term is “hard disk”).
  <II-2>Subtask 2: Aspect term polarity
  For a given set of aspect terms within a sentence, determine whether the polarity of each aspect term is positive, negative, neutral or conflict (i.e., both positive and negative).
  For example:
  “I loved their fajitas” → {fajitas: positive}
  “I hated their fajitas, but their salads were great” → {fajitas: negative, salads: positive}
  “The fajitas are their first plate” → {fajitas: neutral}
  “The fajitas were great to taste, but not to see” → {fajitas: conflict}
  <II-3>Subtask 3: Aspect category detection
  Given a predefined set of aspect categories (e.g., price, food), identify the aspect categories discussed in a given sentence. Aspect categories are typically coarser than the aspect terms of Subtask 1, and they do not necessarily occur as terms in the given sentence.
  For example, given the set of aspect categories {food, service, price, ambience, anecdotes/miscellaneous}:
  “The restaurant was too expensive” → {price}
  “The restaurant was expensive, but the menu was great” → {price, food}
  <II-4>Subtask 4: Aspect category polarity
  Given a set of pre-identified aspect categories (e.g., {food, price}), determine the polarity (positive, negative, neutral or conflict) of each aspect category.
  For example:
  “The restaurant was too expensive” → {price: negative}
  “The restaurant was expensive, but the menu was great” → {price: negative, food: positive}
  
III. Description of Dataset
  <III-1>Restaurant reviews:
  This dataset consists of over 3K English sentences from the restaurant reviews of Ganu et al. (2009). The original dataset of Ganu et al. included annotations for coarse aspect categories (Subtask 3) and overall sentence polarities; we modified the dataset to include annotations for aspect terms occurring in the sentences (Subtask 1), aspect term polarities (Subtask 2), and aspect category polarities (Subtask 4). Additional restaurant reviews, not in the original dataset of Ganu et al. (2009), are being annotated in the same manner, and they will be used as test data.
  <III-2>Laptop reviews:
  This dataset consists of over 3K English sentences extracted from customer reviews of laptops. Experienced human annotators tagged the aspect terms of the sentences (Subtask 1) and their polarities (Subtask 2). This dataset will be used only for Subtasks 1 and 2. Part of this dataset will be reserved as test data.
  <III-3>Dataset format:
  The sentences in the datasets are annotated using XML tags.
  The following example illustrates the format of the annotated sentences of dataset.
  
  <sentence id="813">
    <text>
      All the appetizers and salads were fabulous, the steak was mouth watering and the pasta was delicious!!!
    </text> 
    <aspectTerms>
      <aspectTerm term="appetizers" polarity="positive" from="8" to="18"/> 
      <aspectTerm term="salads" polarity="positive" from="23" to="29"/> 
      <aspectTerm term="steak" polarity="positive" from="49" to="54"/> 
      <aspectTerm term="pasta" polarity="positive" from="82" to="87"/>
    </aspectTerms> 
    <aspectCategories>
      <aspectCategory category="food" polarity="positive"/> 
    </aspectCategories>
  </sentence>
  
  The possible values of the polarity field are: “positive”, “negative”, “conflict”, “neutral”. The possible values of the category field are: “food”, “service”, “price”, “ambience”, “anecdotes/miscellaneous”.
  The format of the annotated sentences of the laptops dataset are same as the restaurant datasets, with the only exception that there are no annotations for aspect categories.
<III-4>Useful Link:
  On the following link we can find all dataset in this project: http://alt.qcri.org/semeval2014/task4/index.php?id=data-and-tools
  
IV. How We Use the Dataset
  <IV-1> Based on train, test and trial
  <a> For the training data:
  We use them to “train” some useful tools designed by ourselves. Both restaurant and laptop reviews are useful.
  <b> For the testing data:
  We use them to get outcomes of this project. Both restaurant and laptop reviews are useful.
  <c> For the trial data:
  We use to estimate our methods and evaluate its accuracy. But only restaurant reviews are useful because the laptop reviews are incomplete.
  <IV-2> Based on type of dataset
  <a>Restaurant data
  Using for all subtasks, to extract aspect terms, extract aspect categories, then determine their corresponding polarities,
  <b>Laptop data
  Using for only subtask1 and 2, since this type of dataset does not have aspect categories, then subtask3 and 4 is meaningless in this kind of dataset.
  <IV-3> Based on given original files
  <a> In training dataset, their are totally 2 version of data, we use the second version of training data since the second version have modified some little error of the first version.
  <b> In testing dataset, there are two phases of data for each type of dataset, we use both of them since phase A are raw texts, which we can use in subtask1 and 3, and phase B are text with given aspect terms and categories, which we can use in subtask2 and 4 directly and do not need to use outcomes of subtask1 and 3 to analyze polarity.
  
