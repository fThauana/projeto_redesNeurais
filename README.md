# 🛒 Amazon Sentiment Analysis com Redes Neurais

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.0%2B-orange)
![Type](https://img.shields.io/badge/Academic-Project-lightgrey)

> Projeto acadêmico desenvolvido para a disciplina de **Data Science**.
> Um modelo de Deep Learning capaz de classificar avaliações e decidir quando acionar um humano.

---

## 📄 Sobre o Projeto

Este projeto foi desenvolvido em dupla como requisito acadêmico. O objetivo foi criar um sistema automatizado para análise de sentimento de avaliações de produtos da Amazon, utilizando Processamento de Linguagem Natural (NLP).

O grande diferencial que implementamos foi uma **Camada de Decisão de Negócio**. Não buscamos apenas a acurácia técnica, mas sim simular um ambiente real onde o modelo avalia sua própria "certeza" para separar casos complexos para revisão manual.

---

## 🛠️ Tecnologias Utilizadas

* **Linguagem:** Python
* **Machine Learning:** TensorFlow / Keras (Redes Neurais), Scikit-Learn
* **NLP:** TF-IDF (Term Frequency-Inverse Document Frequency)
* **Processamento de Dados:** Pandas, NumPy
* **Visualização:** Matplotlib, Seaborn

---

## 🧠 Arquitetura da Rede Neural

Utilizamos uma arquitetura **Multilayer Perceptron (MLP)** construída com a API Sequential do Keras:

1.  **Camada de Entrada:** Recebe 5000 features vetorizadas (TF-IDF).
2.  **Camadas Ocultas (Dense):**
    * 128 Neurônios (ReLU) + Dropout (0.5)
    * 64 Neurônios (ReLU) + Dropout (0.5)
    * *O Dropout foi aplicado para mitigar o Overfitting durante o treinamento.*
3.  **Camada de Saída:** 1 Neurônio com ativação **Sigmoid** (retorna a probabilidade).

---

## 📊 Estratégia de Negócio (Nosso Diferencial)

Definimos regras de corte baseadas na probabilidade predita pelo modelo para otimizar o fluxo de trabalho:

<div align="center">
  <img alt="Gráfico de Distribuição de Probabilidades" width="700" src="https://github.com/user-attachments/assets/7e60e32f-d4ef-47b8-b4db-a6b3525bc93b" />
  <br>
  <em>Distribuição de probabilidade e zonas de corte definidas pela equipe</em>
</div>

### Regras Implementadas:

| Probabilidade | Classificação | Ação do Sistema | Risco |
| :--- | :--- | :--- | :--- |
| **< 10%** | Negativo | **Automática** (Classificar como Ruim) | Baixo |
| **10% - 90%** | Incerto | **Transbordo** (Enviar p/ Análise Humana) | N/A |
| **> 90%** | Positivo | **Automática** (Classificar como Bom) | Baixo |

---

## 📈 Resultados Alcançados

O modelo foi avaliado em um dataset de teste balanceado:

* **Acurácia Global:** 80%
* **AUC-ROC Score:** 0.89

---

## 👥 Autores

<table>
  <tr>
    <td align="center">
      <a href="https://www.linkedin.com/in/thauana-vitoria-ferreira-farias">
        <img src="https://github.com/fThauana.png" width="100px;" alt="Foto Thauana"/><br>
        <sub>
          <b>Thauana Farias</b>
        </sub>
      </a>
    </td>
    <td align="center">
      <a href="https://www.linkedin.com/in/jaysie-oliveira-712490253/">
        <img src="https://github.com/jayjbo.png" width="100px;" alt="Foto Dupla"/><br>
        <sub>
          <b>Jaysie Oliveira</b>
        </sub>
      </a>
    </td>
  </tr>
</table>
