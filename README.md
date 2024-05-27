# Sentiment analytics - Transformers TensorFlow

Dane pochodzą z IMDb Non-Commercial Datasets. Zawierają pięćdziesiąt
tysięcy recenzji od krytyków filmowych i są oznaczone odpowiednio jako
pozytywne i negatywne. Usunięte zostały tagi HTML (nie wnoszą żadnych potrzebnych informacji),
znaki interpunkcyjne (mogą powodować szumy w danych), stopwordsy (to
słowa które często występują bardzo często w tekście i nie są istotne przy
samym modelu). Użycie tokenizacji – podział tekstu na poszczególne słowa w recenzjach.
Następnie sekwencje – zamiana tych słów w reprezentację liczbowe (modele
pracują na danych liczbowych).
Word embedding przy użyciu GloVe – skupienie się na kontekście danego
słowa i powiązaniach z innymi wyrazami (globalnie w przypadku GloVe).

Pierwszy model to konwolucyjna sieć neuronowa gdzie warstwą wejściową
jest zwektoryzowany tekst przy użyciu GloVe, następnie dodawane są
warstwy konwolucyjne z funkcją aktywacji ReLU dzięki czemu wydobywane
są cechy (GlobalMaxPooling1D wydobywa cechy najważniejsze). Finalnie
zachodzi klasyfikacja binarna (Sigmoid).
Finalnie dane są testowane za pomocą pięciokrotnej cross-validacji. Po każdej
epoce mierzona jest dokładność modelu.

Model drugi to Fine-Tuned GPT-2 oraz odpowiadający mu tokenizer z
biblioteki transformers. Model jest już wytrenowany na dużym zbiorze
danych, a następnie jest on dopasowywany do konkretnej klasyfikacji.
Dla każdej recenzji tekst jest kodowany przy użyciu GPT2Tokenizer a
następnie przekazywany do modelu który przewiduje jaki jest sentyment
odpowiedniej recenzji.
