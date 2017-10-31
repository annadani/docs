---
layout: base
title:  'Working Group on Comparatives'
udver: '2'
---

# Working Group on Comparative Constructions

A prototypical comparative construction involves a quality or property whose
extent is compared, the entity being compared, and the standard of comparison.
Thus in [en] _Stephan is taller than Joakim,_ Stephan is the entity compared,
Joakim represents the standard of comparison to which Stephan is compared,
and the adjective _taller_ denotes the quality that is compared, i.e.,
tallness.

Adverbs can be compared as well, e.g. in
[cs] _Michal mluví lépe než Miloš_ “Michal speaks better than Miloš”,
the word _lépe_ is an adverb and it denotes the quality of Michal's speaking
rather than of his personality in general.

Finally, we can also compare quantities, as in
_Melanie has more money than Sue,_ or in
_There is more than one way of doing it;_
in the latter example, the standard of comparison is conflated with the entity
counted. Similarly, there are sentences where both the standard of comparison
and the new value are hidden in the verb:
_The prices of homes have more than doubled._

The syntax of comparative constructions poses various challenges for linguistic
theory. For English, many of these are discussed in Bresnan (1973) and
Huddleston and Pullum (2002, chapter 13). A cross-linguistic survey of equality
comparison is provided in Haspelmath (2017).

There are no UD relations designed specifically to mark comparative
constructions. This page documents what regular UD means are used to analyze
these constructions and how they are applied.

## Equality, Direction and Degree

* Equality comparison [en]: _The car is as big as mine._
* Equality comparison [cs]: _To auto je stejně velké jako moje._ “The car is as big as mine.” Alternatives: _To auto je tak velké jako moje. To auto je velké jako moje._
* Similarity comparison [cs]: _To auto je podobně velké jako moje._ “The car is similarly big to mine.”
* Inequality non-scalar comparison [cs]: _To auto je jinak velké než moje._ “The car's size is different from mine.” (lit. “The car is differently big than mine.”)
* Scalar decreasing comparison (inferiority) [cs]: _Loňský model byl méně propracovaný než letošní._ “The last year's model was less elaborated than this year's.”
* Scalar increasing comparison (superiority) [cs]: _Letošní model je propracovanější než loňský._ “This year's model is more elaborated than last year's.”
* Superlative [en]: _This is the biggest car of all._
* Superlative [cs]: _Tohle je největší auto ze všech._ “This is the biggest car of all.”
* Decreasing superlative [cs]: _Letošní model je nejméně propracovaný za posledních pět let._ “This year's model is the least elaborated of the previous five years.”

## Coding Strategies across Languages

### Morphological Gradation of Adjectives and Adverbs

Adjectives in some languages have an inflectional category that expresses
degree of comparison. Special forms are used when the adjective appears in
an inequality scalar comparison: A form called _comparative_ is used when
the modified noun has a greater degree of the quality denoted by the adjective
than the standard of comparison. A form called _superlative_ is used when
the modified noun has a greater degree of the quality denoted by the adjective
than all entities in a certain set. In UD, morphological comparatives and
superlatives are tagged using the [Degree]() feature: `Degree=Cmp` and `Degree=Sup`,
respectively. If a language has morphological comparative and/or superlative,
then the base forms of ajdectives should be tagged as the _positive_ degree
(`Degree=Pos`). Note that the positive degree should not be confused with the
positive [Polarity](). Even negative adjectives can be compared, therefore they
can also have the positive (basic) degree.

Czech:

~~~ conllu
1	Martin	Martin	PROPN	_	Case=Nom|Gender=Masc|Number=Sing	3	nsubj	_	Gloss=Martin
2	je	být	AUX	_	Mood=Ind|Number=Sing|Person=3|Tense=Pres|VerbForm=Fin|Voice=Act	3	cop	_	Gloss=is
3	inteligentní	inteligentní	ADJ	_	Case=Nom|Degree=Pos|Gender=Masc|Number=Sing	0	root	_	Gloss=intelligent|SpaceAfter=No
4	.	.	PUNCT	_	_	3	punct	_	Gloss=.

~~~

~~~ conllu
1	Martin	Martin	PROPN	_	Case=Nom|Gender=Masc|Number=Sing	3	nsubj	_	Gloss=Martin
2	je	být	AUX	_	Mood=Ind|Number=Sing|Person=3|Tense=Pres|VerbForm=Fin|Voice=Act	3	cop	_	Gloss=is
3	inteligentnější	inteligentní	ADJ	_	Case=Nom|Degree=Cmp|Gender=Masc|Number=Sing	0	root	_	Gloss=more-intelligent
4	než	než	SCONJ	_	_	5	case	_	Gloss=than
5	Vojta	Vojta	PROPN	_	Case=Nom|Gender=Masc|Number=Sing	3	obl	_	Gloss=Vojta|SpaceAfter=No
6	.	.	PUNCT	_	_	3	punct	_	Gloss=.

~~~

~~~ conllu
1	Martin	Martin	PROPN	_	Case=Nom|Gender=Masc|Number=Sing	3	nsubj	_	Gloss=Martin
2	je	být	AUX	_	Mood=Ind|Number=Sing|Person=3|Tense=Pres|VerbForm=Fin|Voice=Act	3	cop	_	Gloss=is
3	nejinteligentnější	inteligentní	ADJ	_	Case=Nom|Degree=Sup|Gender=Masc|Number=Sing	0	root	_	Gloss=most-intelligent
4	ze	z	ADP	_	_	5	case	_	Gloss=of
5	všech	všechen	PRON	_	Case=Gen|Gender=Masc|Number=Plur|PronType=Tot	3	obl	_	Gloss=all|SpaceAfter=No
6	.	.	PUNCT	_	_	3	punct	_	Gloss=.

~~~

~~~ conllu
1	Vyšetření	vyšetření	NOUN	_	Case=Nom|Gender=Neut|Number=Sing|VerbForm=Vnoun	3	nsubj	_	Gloss=exam
2	je	být	AUX	_	Mood=Ind|Number=Sing|Person=3|Tense=Pres|VerbForm=Fin|Voice=Act	3	cop	_	Gloss=is
3	nepříjemné	příjemný	ADJ	_	Case=Nom|Degree=Pos|Gender=Neut|Number=Sing|Polarity=Neg	0	root	_	Gloss=unpleasant|SpaceAfter=No
4	,	,	PUNCT	_	_	8	punct	_	Gloss=,
5	ale	ale	CCONJ	_	_	8	cc	_	Gloss=but
6	operace	operace	NOUN	_	Case=Nom|Gender=Fem|Number=Sing	8	nsubj	_	Gloss=surgery
7	je	být	AUX	_	Mood=Ind|Number=Sing|Person=3|Tense=Pres|VerbForm=Fin|Voice=Act	8	cop	_	Gloss=is
8	nepříjemnější	příjemný	ADJ	_	Case=Nom|Degree=Cmp|Gender=Fem|Number=Sing|Polarity=Neg	3	conj	_	Gloss=more-unpleasant|SpaceAfter=No
9	.	.	PUNCT	_	_	3	punct	_	Gloss=.

~~~

Similarly, the degree morphology also applies to Czech adverbs:

~~~ conllu
1	Martin	Martin	PROPN	_	Case=Nom|Gender=Masc|Number=Sing	2	nsubj	_	Gloss=Martin
2	běhá	běhat	VERB	_	Mood=Ind|Number=Sing|Person=3|Tense=Pres|VerbForm=Fin|Voice=Act	0	root	_	Gloss=runs
3	rychle	rychle	ADV	_	Degree=Pos|Polarity=Pos	2	advmod	_	Gloss=fast|SpaceAfter=No
4	.	.	PUNCT	_	_	2	punct	_	Gloss=.

~~~

~~~ conllu
1	Martin	Martin	PROPN	_	Case=Nom|Gender=Masc|Number=Sing	2	nsubj	_	Gloss=Martin
2	běhá	běhat	VERB	_	Mood=Ind|Number=Sing|Person=3|Tense=Pres|VerbForm=Fin|Voice=Act	0	root	_	Gloss=runs
3	rychleji	rychle	ADV	_	Degree=Cmp|Polarity=Pos	2	advmod	_	Gloss=faster
4	než	než	SCONJ	_	_	5	case	_	Gloss=than
5	Vojta	Vojta	PROPN	_	Case=Nom|Gender=Masc|Number=Sing	3	obl	_	Gloss=Vojta|SpaceAfter=No
6	.	.	PUNCT	_	_	2	punct	_	Gloss=.

~~~

~~~ conllu
1	Martin	Martin	PROPN	_	Case=Nom|Gender=Masc|Number=Sing	2	nsubj	_	Gloss=Martin
2	běhá	běhat	VERB	_	Mood=Ind|Number=Sing|Person=3|Tense=Pres|VerbForm=Fin|Voice=Act	0	root	_	Gloss=runs
3	nejrychleji	rychle	ADV	_	Degree=Sup|Polarity=Pos	2	advmod	_	Gloss=fastest
4	ze	z	ADP	_	_	5	case	_	Gloss=of
5	všech	všechen	PRON	_	Case=Gen|Gender=Masc|Number=Plur|PronType=Tot	3	obl	_	Gloss=all|SpaceAfter=No
6	.	.	PUNCT	_	_	2	punct	_	Gloss=.

~~~

There are also languages with morphologically expressed equative degree, used
in equality comparisons. One such language is Hiligaynon [hil] (Philippinic;
Wolfenden 1971:103) Haspelmath (2017):

“Pedro is handsome.”

~~~ conllu
1	Si	si	ADP	_	_	2	case	_	Gloss=TOPIC
2	Pedro	Pedro	PROPN	_	_	3	nsubj	_	Gloss=Pedro
3	gwapo	gwapo	ADJ	_	Degree=Pos	0	root	_	Gloss=handsome|SpaceAfter=No
4	.	.	PUNCT	_	_	3	punct	_	Gloss=.

~~~

“Pedro is as handsome as Juan.”

~~~ conllu
1	Si	si	ADP	_	_	2	case	_	Gloss=TOPIC
2	Pedro	Pedro	PROPN	_	_	3	nsubj	_	Gloss=Pedro
3	kasinggwapo	gwapo	ADJ	_	Degree=Equ	0	root	_	Gloss=as-handsome
4	ni	ni	ADP	_	_	5	case	_	Gloss=of
5	Juan	Juan	PROPN	_	_	3	obl	_	Gloss=Juan|SpaceAfter=No
6	.	.	PUNCT	_	_	3	punct	_	Gloss=.

~~~

### Periphrastic Gradation

Other languages, like English, have a mixed system. Some English adjectives
have morphological degrees like in Czech, e.g., _smart – smarter – smartest._
Other adjectives must be compared periphrastically with the help of the words
_more, most, less_ and _least._ These function words provide the degree
feature and they can be viewed themselves as (irregular) degree forms of two
basic adverbs: _much – more – most; little – less – least._

~~~ conllu
1	Martin	Martin	PROPN	_	Gender=Masc|Number=Sing	3	nsubj	_	_
2	is	be	AUX	_	Mood=Ind|Number=Sing|Person=3|Tense=Pres|VerbForm=Fin	3	cop	_	_
3	more	much	ADV	_	Degree=Cmp	4	advmod	_	_
4	intelligent	intelligent	ADJ	_	Degree=Pos	0	root	_	_
5	than	than	SCONJ	_	_	6	case	_	_
6	Donald	Donald	PROPN	_	Gender=Masc|Number=Sing	4	obl	_	SpaceAfter=No
7	.	.	PUNCT	_	_	4	punct	_	_

~~~

~~~ conllu
1	Martin	Martin	PROPN	_	Gender=Masc|Number=Sing	3	nsubj	_	_
2	is	be	AUX	_	Mood=Ind|Number=Sing|Person=3|Tense=Pres|VerbForm=Fin	3	cop	_	_
3	the	the	DET	_	Definite=Def|PronType=Art	6	_	_
4	most	much	ADV	_	Degree=Sup	5	advmod	_	_
5	intelligent	intelligent	ADJ	_	Degree=Pos	6	amod	_	_
6	guy	guy	NOUN	_	Number=Sing	0	root	_	_
7	of	of	ADP	_	_	8	case	_	_
8	all	all	PRON	_	PronType=Tot	5	obl	_	SpaceAfter=No
9	.	.	PUNCT	_	_	6	punct	_	_

~~~

The comparative and superlative represent increasing degrees of the quality
compared. Decreasing degrees can also be expressed, e.g., instead of saying
that _Martin is more intelligent than Donald,_ we could say that _Donald is
less intelligent than Martin._ The coding of decreasing degrees is
periphrastic even in Czech:

~~~ conllu
1	Vojta	Vojta	PROPN	_	Case=Nom|Gender=Masc|Number=Sing	4	nsubj	_	Gloss=Vojta
2	je	být	AUX	_	Mood=Ind|Number=Sing|Person=3|Tense=Pres|VerbForm=Fin|Voice=Act	4	cop	_	Gloss=is
3	méně	málo	ADV	_	Degree=Cmp|Polarity=Pos	4	advmod	_	Gloss=less
4	inteligentní	inteligentní	ADJ	_	Case=Nom|Degree=Pos|Gender=Masc|Number=Sing	0	root	_	Gloss=intelligent
5	než	než	SCONJ	_	_	6	case	_	Gloss=than
6	Martin	Martin	PROPN	_	Case=Nom|Gender=Masc|Number=Sing	4	obl	_	Gloss=Martin|SpaceAfter=No
7	.	.	PUNCT	_	_	4	punct	_	Gloss=.

~~~