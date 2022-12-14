Built whilst I was getting to documenting the organsisms I was working on in DTOL this little project allowed me to get to: know the Obsidian environment a bit better, improve my skills in JavaScript and create a local database on the bugs I like (bees and wasps).

#### GitHub
[Here](https://github.com/DLBPointon/QuickAdd-ncbi)

#### Tech Stack
| Technology | Docs | Implimented | Description | 
|--|--|--|--|
| JavaScript | | Done | Language |
| Markdown | | Done | Language |
| Obsidian | | Done | Knowledge management software |

#### Output
```
# Tiphia femorata

## Taxonomic Data
### TaxID:: 330862
### RankOfQuery:: species
### Lineage:: [[Eukaryota]], [[Metazoa]], [[Ecdysozoa]], [[Arthropoda]],
                [[Hexapoda]], [[Insecta]], [[Pterygota]], [[Neoptera]],
                [[Endopterygota]], [[Hymenoptera]], [[Apocrita]], [[Aculeata]],
                [[Tiphioidea]], [[Tiphiidae]], [[Tiphiinae]], [[Tiphia]], [[]]

## Genetic Code
### GeneticCode:: 1
### MitoGeneticCode:: 5
```

This allows for each segment of the lineage to create a linked mention to another note and using a Plugin called DataView you would be able to collate all Aprocrita, for example, you are working on.

#### Future work

[[NCBI-Notes]]
Currently the scope of this pseudo plugin is limited to the taxonomic data that ncbi has on an organism, this is just a fraction of the whole API. I would like to create a stand alone Plugin that can query the API and generate a note with data denoted in a template.

I'm aware that the user base for such a Plugin will be limited to the handful of bioinformaticians that use Obsidian but it gives the chance to understand the Obsidian API, JavaScript and NCBI API.