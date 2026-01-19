# 🛡️ GDPR-Ontology: A Semantic Framework for Data Privacy Compliance

[![Ontology](https://img.shields.io/badge/Ontology-OWL%20%2F%20RDF-blue.svg)](https://www.w3.org/OWL/)
[![RML](https://img.shields.io/badge/Data%20Mapping-RML-red.svg)](https://rml.io/)

## 📖 Project Overview
The **GDPR-Ontology** project provides a formal, semantic representation of the **General Data Protection Regulation (GDPR)**. By translating complex legal texts into a machine-readable format, this framework enables automated compliance auditing, logical reasoning, and efficient management of data privacy.

**Academic Context:**
* **Institution:** Alexandria University, Institute of Graduate Studies and Research (IGSR), Information Technology Department.
* **Course:** Web-Based Information Systems.

## ✨ Key Features
- **Formal Knowledge Representation:** Bridges the gap between legal requirements and technical system operations.
- **Semantic Data Transformation:** Integrates **RML (RDF Mapping Language)** to convert tabular data (CSV) into a structured Knowledge Graph.
- **Automated Reasoning:** Designed to work with reasoners (like HermiT) to detect compliance gaps and inconsistencies.
- **Test-Ready Dataset:** Includes a sample CSV with **20 dummy records** representing various data processing scenarios.

## 🏗️ Ontology Design
The model is structured around key GDPR concepts and existing semantic web standards:
* **Classes:** `DataProcessingActivity`, `DataSubject`, `DataController`, `LegalBasis`, and `PersonalDataCategory`.
* **Vocabulary Reuse:** Human entities are aligned with `foaf:Person` to enhance interoperability.
* **Logic & Constraints:** * **Disjointness:** Ensures that entities like `DataController` and `DataProcessor` are distinct.
    * **Cardinality:** Enforces rules such as every activity having exactly one `LegalBasis`.
    * **Domain & Range:** Strictly defines how properties link different classes.

## 🛠️ Components & Tools
- **Ontology File:** The core schema (TTL) defining the GDPR domain logic.
- **RMLMapper Engine:** `rmlmapper-8.0.0-r378-all.jar` — used to execute mapping rules.
- **Mapping File:** `mapping.ttl` — defines the transformation logic from CSV to RDF.
- **Dataset:** `data.csv` — 20 records of simulated processing activities for validation.

## 🚀 Execution & Transformation
To transform the provided dummy data into a semantic Knowledge Graph, run the following command in your terminal:

```bash
java -jar rmlmapper-8.0.0-r378-all.jar --mappingfile mapping.ttl --outputfile output.ttl
```
## 🔍 SPARQL Compliance Queries

The ontology supports complex querying to verify regulatory adherence.  
Below are the primary queries used for evaluation:

### 1. Identify Standard Processing (Article 6)
Retrieves activities governed by the general legal framework.

```sparql
PREFIX : <http://www.semanticweb.org/maryam/ontologies/2024/11/gdpr#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>

SELECT ?Activity_ID ?Activity_Name
WHERE {
  ?activity rdf:type :DataProcessingActivity ;
            :isGovernedBy :Article_6 ;
            :activityName ?Activity_Name .
}
```
### 2. Find Activities Requiring "Explicit Consent"

Identifies processes involving sensitive data that strictly require explicit consent.

```sparql
PREFIX : <http://www.semanticweb.org/maryam/ontologies/2024/11/gdpr#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>

SELECT ?Activity_Name ?Category
WHERE {
  ?activity :requiresBasis :Explicit_Consent ;
            :activityName ?Activity_Name ;
            :processes ?Category .
}
```
### 3. Identify Activities Based on Contract

Lists activities justified by the fulfillment of a contract.

```sparql
PREFIX : <http://www.semanticweb.org/maryam/ontologies/2024/11/gdpr#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>

SELECT ?Activity_Name ?Basis
WHERE {
  ?activity :requiresBasis :Contract ;
            :activityName ?Activity_Name .
}
```
## ✅ Evaluation & Validation

The ontology has been successfully validated using the **HermiT 1.4.3.456** reasoner in **Protégé**.  
The model is confirmed to be **logically consistent**, meaning that all classes, properties, and instances adhere to the defined GDPR constraints without contradiction.
