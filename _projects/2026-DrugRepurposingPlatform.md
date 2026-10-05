---
title: Drug Repurposing Platform
summary: A neurosymbolic drug-repurposing framework that integrates heterogeneous biomedical knowledge graphs into a unified knowledge representation. The framework combines symbolic KG retrieval through SPARQL/Cypher with sAIM-based GNN link prediction to identify both established and potentially novel drug–disease associations. Candidate associations are ranked by combining KG-derived evidence with predictive confidence, while each prediction is accompanied by supporting reasoning paths, provenance, confidence scores, and human-readable explanations to enable transparent and interpretable drug-repurposing decisions.
area: AI in Pharma
status: active
featured: true
duration: 2026 - Present
order: 20
paper_key: drug-repurposing
contact: madhur.thareja@iairo.ai
---

Project Motive

Drug repurposing offers a potentially faster and more cost-effective route to identifying new treatments by discovering alternative therapeutic applications for existing drugs. However, biomedical evidence is distributed across heterogeneous knowledge sources, including drug–disease, drug–target, gene–disease, protein–protein, and pathway relationships. Conventional retrieval approaches often surface individual facts without connecting them into a coherent chain of evidence, while purely neural link-prediction systems can produce plausible associations that are difficult to interpret or validate.


The Pharma Drug Repurposing Platform addresses this gap through a neurosymbolic approach that combines the complementary strengths of symbolic and neural reasoning. Knowledge-graph queries provide explicit, traceable evidence and multi-hop reasoning paths, while GNN-based models learn latent structural patterns in the biomedical graph to identify missing or potentially novel associations. This creates a discovery pipeline in which predictions can be ranked, traced back to their supporting evidence, and presented in a form suitable for human validation.


Current open threads include expanding and harmonizing biomedical knowledge graph sources, improving GNN-based link prediction and candidate ranking, validating novel drug–disease associations against external evidence, and developing a scalable human-in-the-loop workflow for biomedical researchers.
