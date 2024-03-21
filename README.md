[English below](#verbal-nominal-dependency-parser)

# Parsiwr Dibyniaethau Enwol / Berfol
Parsiwr dibyniaethau arbrofol sy'n ceisio gwahaniaethu rhwng defnydd enwol a berfol o'r berfenw. Ar sail UD_CCG: https://github.com/UniversalDependencies/UD_Welsh-CCG/ .

Gweler yma am ragor o wybodaeth am y cymhellaid: https://github.com/techiaith/parsiwr-dibyniaethau

Er mwyn defnyddio’r gydran hon, bydda angen i chi yn gyntaf osod llyfrgell spaCy (https://spacy.io/usage), ac yna gosod y pecyn iaith Cymraeg o https://github.com/techiaith/spacy-lang-cy.

Unwaith y bydd rheini wedi eu gosod gennych, gallwch osod y model fel a ganlyn drwy lwytho'r pecyn i lawr a llywio i'r cyfeiriadur lle cafodd y ffeil ei lawrlwytho a rhedeg:

`pip install cy_model0-0.0.0.tar.gz` 

Yna, o fewn sgript Python, gallwch lwytho’r model fel a ganlyn:

```
import spacy

nlp = spacy.load("cy_model")
doc = nlp("roedd yn rhyfeddu mor dda oedd y canu")
print ([(t.text, t.tag_) for t in doc])

```
Bydd y canlyniadau wedyn yn gwahaniaethu rhwng berfenw berfol fel yn _yn rhyfeddu_ ac un enwol fel yn _y canu_.
```
>>> [('roedd', 'auxverb'),
     ('yn', 'impf'),
     ('rhyfeddu', 'verbal_vn'),
     ('mor', 'adv'),
     ('dda', 'pos'),
     ('oedd', 'aux'),
     ('y', 'art'),
     ('canu', 'nominal_vn')]
```

I ddelweddu’r parsiad, defnyddiwch y canlynol:

```
import spacy
from spacy import displacy

nlp = spacy.load("cy_model")
doc = nlp("roedd yn rhyfeddu mor dda oedd y canu")
displacy.serve(doc, style="dep")

>>> Using the 'dep' visualizer
Serving on http://0.0.0.0:5000 ...
```
Wedyn, bydd modd i chi ymweld â http://0.0.0.0:5000 a gweld y delweddiad canlynol:

![berfenwau_enwol_a_berfol](https://github.com/techiaith/parsiwr_dibyniaethau_enwol_berfol/assets/10194573/3e40ae8f-751f-49f3-97cb-908ec81bb473)

Diolch i Lywodraeth Cymru am ariannu'r gwaith hwn fel rhan o broject Technoleg Cymraeg 2023-24. 

# Verbal / Nominal Dependency Parser
An experimental dependency parser which attempts to differentiate between nominal and verbal verbnouns.Based on UD_CCG.

See here for more information regarding the underlying motivation: https://github.com/techiaith/parsiwr-dibyniaethau

![berfenwau_enwol_a_berfol](https://github.com/techiaith/parsiwr_dibyniaethau_enwol_berfol/assets/10194573/3e40ae8f-751f-49f3-97cb-908ec81bb473)
