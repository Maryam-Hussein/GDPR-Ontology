# 🛡️ GDPR-Ontology: A Semantic Framework for Data Privacy

[![Ontology](https://img.shields.io/badge/Ontology-OWL%20%2F%20RDF-blue.svg)](https://www.w3.org/OWL/)
[![RML](https://img.shields.io/badge/Data%20Mapping-RML-red.svg)](https://rml.io/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## 📖 Overview

The **GDPR-Ontology** project provides a formal, semantic representation of the **General Data Protection Regulation (GDPR)**. This repository bridges the gap between complex legal requirements and automated technical systems by providing the ontology structure, mapping rules, and the necessary tools to transform raw data into a GDPR-compliant Knowledge Graph.

## ✨ Key Features

- **Comprehensive Modeling:** Covers core GDPR entities including Data Subjects, Controllers, and Processors.
- **Semantic Mapping:** Uses RML (RDF Mapping Language) to transform traditional data formats into semantic triples.
- **Automated Transformation:** Includes a ready-to-use execution engine (RMLMapper).
- **Test-Ready:** Comes with pre-configured dummy data to demonstrate the workflow.

## 🛠️ Components & Tools

This repository is self-contained and includes:

1. **Ontology File:** The core `.owl` file representing the GDPR domain logic.
2. **RMLMapper Tool:** `rmlmapper-8.0.0-r378-all.jar` — a Java-based engine used to execute RML mapping rules.
   * *Source:* [RMLio/rmlmapper-java](https://github.com/RMLio/rmlmapper-java/releases).
3. **Mapping Rules:** `mapping.ttl` defines the relationship between the input CSV data and the ontology classes.
4. **Test Data:** A sample CSV file containing **20 dummy records** (Data subjects, consent types, and processing activities) for testing.

## 🚀 Getting Started

### Prerequisites
- **Java Runtime Environment (JRE):** Ensure you have Java 8+ installed.
- **Protégé:** (Optional) Recommended for visualizing the generated Knowledge Graph.

### Data Transformation (CSV to RDF)
To transform the provided dummy data into a semantic RDF format (Turtle), run the following command in your terminal:

```bash
java -jar rmlmapper-8.0.0-r378-all.jar --mappingfile mapping.ttl --outputfile output.ttl
