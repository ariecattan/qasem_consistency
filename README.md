# QASemConsistency

This repo includes the code and dataset for the paper: [Localizing Factual Inconsistencies in Attributable Text Generation](https://arxiv.org/abs/2410.07473)


# Data

Our dataset can be found under the `data` folder. 

Each instance includes a `JSON` object with the following fields:
```json
{
    "source_id": "",
    "source": [], // list of tokens of the grounding 
    "summary": [], // list of sentences in the response
    "model": "", // name of model that generates the response
    "datasource": "", 
    "dataset": "", // cliff, factscore or verifiability
    "spans": [], // list of spans (see below)
    "qas": [], // list of qas (see below)
}
```

Each `span` is a JSON object that appears in the form:
```json
{
    "id": 1, 
    "start": 7, 
    "end": 8, 
    "qaIds": [1], // IDs of QAs involving this span
    "annotations": [1, 1, 1] // raw annotations, 1 is covered, 0 is hallucinated
}
```

Each `qa` is a JSON object that appears in the form:
```json
{
    "qa_id": 2,
    "sent_id": 0, 
    "predicate_idx": 8, 
    "predicate_pos": "VERB", 
    "predicate": "missing", 
    "question": "who was missing?", 
    "answer_idx": "3-6", 
    "answer": "an Alabama boy", 
    "annotations": [0, 0, 0] // here 0 is supported and 1 is hallucinated
}
```

# Models

Our QASem parsers can be found here: https://github.com/plroit/qasem_parser

T5-XL: https://huggingface.co/cattana/flan-t5-xl-qasem-joint-tokenized  
T5-Large: https://huggingface.co/cattana/flan-t5-large-qasem-joint-tokenized

# Citation

```bash
@article{Cattan2024LocalizingFI,
  title={Localizing Factual Inconsistencies in Attributable Text Generation},
  author={Arie Cattan and Paul Roit and Shiyue Zhang and David Wan and Roee Aharoni and Idan Szpektor and Mohit Bansal and Ido Dagan},
  journal={ArXiv},
  year={2024},
  volume={abs/2410.07473},
}   
```
