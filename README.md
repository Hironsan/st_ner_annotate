# Streamlit Named Entity Recognition (NER) Annotation component

This is a component to assist with the annotation of *named entities* in an unstructured piece of text.

![Streamlit NER Annotate Demo GIF](https://raw.githubusercontent.com/Hironsan/st_ner_annotate/master/docs/st_ner_annotate_demo.gif)

## Installation

```bash
pip install st-ner-annotate
```

## Usage

Save the following code as `app.py` and run it with `streamlit run app.py`.

```python
import streamlit as st
from st_ner_annotate import st_ner_annotate

st.title("Named entity recognition demo")
text = """Manhattan traces its origins to a trading post founded by colonists 
    from the Dutch Republic in 1624 on Lower Manhattan; the post was named New 
    Amsterdam in 1626. Manhattan is historically documented to have been purchased 
    by Dutch colonists from Native Americans in 1626 for 60 guilders, which equals 
    roughly $1059 in current terms. The territory and its surroundings came under 
    English control in 1664 and were renamed New York after King Charles II of 
    England granted the lands to his brother, the Duke of York. New York, based 
    in present-day Manhattan, served as the capital of the United States from 1785 
    until 1790. The Statue of Liberty greeted millions of immigrants as they came 
    to America by ship in the late 19th century and is a world symbol of the United 
    States and its ideals of liberty and peace. Manhattan became a borough during 
    the consolidation of New York City in 1898."""

entity_labels = ["LOC", "PERSON", "ORG", "MISC"]
ents = []

current_entity_type = st.selectbox("Mark for Entity Type", entity_labels)
entities = st_ner_annotate(current_entity_type, text, ents, key=42)
st.json(entities)
```
