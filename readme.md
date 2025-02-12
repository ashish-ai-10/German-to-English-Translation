# 🇩🇪➜🇬🇧 German-to-English Translation Model  

This project implements a **Neural Machine Translation (NMT) model** using a **sequence-to-sequence (seq2seq) Encoder-Decoder architecture** with **GRU layers**. The model translates sentences from **German** to **English**.

---

## 🚀 Features  
✔️ Implements **Encoder-Decoder** architecture using **TensorFlow & Keras**  
✔️ Uses **Gated Recurrent Units (GRU)** for sequential text processing  
✔️ **Custom Tokenizer** for efficient text preprocessing  
✔️ **Start (`<start>`) & End (`<end>`) tokens** for sequence learning  
✔️ Trained on the **Europarl dataset** with **50,000 sentence pairs**  

---

## 📊 Model Architecture  

The translation model follows a **sequence-to-sequence (seq2seq) architecture** with an **Encoder-Decoder** structure.

### **1️⃣ Encoder**  
The **encoder** processes the input German sentence and generates a **context vector** that summarizes the sequence.  

- **Embedding Layer:** Converts words into dense vectors (`128` dimensions).  
- **3 Stacked GRU Layers:** Extract contextual dependencies and generate a **context vector**.  
- The **final hidden state** of the last GRU layer is passed to the **decoder** as an initial state.  

📌 **Purpose:** Encodes the German sentence into a fixed-length representation.  

---

### **2️⃣ Decoder**  
The **decoder** generates the English translation **word by word**, using the **context vector** from the encoder.  

- **Embedding Layer:** Converts the English tokens into dense vectors.  
- **3 Stacked GRU Layers:** Process the input tokens and generate output sequences.  
- **Dense Layer with Softmax Activation:** Predicts the probability distribution of the next word.  

📌 **Purpose:** Decodes the German sentence into an English translation.  

---

### **3️⃣ Model Flow**  
1. The **encoder** takes the German sentence and generates a **context vector**.  
2. The **decoder** uses this context vector and an initial `<start>` token to generate words.  
3. It predicts the next word in the English sentence **sequentially** until the `<end>` token is reached.  

---

### **4️⃣ Model Summary**  

| Component       | Layers & Features |
|----------------|------------------|
| **Encoder**    | Embedding Layer → 3 GRU Layers → Context Vector |
| **Decoder**    | Embedding Layer → 3 GRU Layers → Dense Layer (Softmax) |
| **Activation** | Softmax (for final output word selection) |
| **Loss Function** | Sparse Categorical Crossentropy |
| **Optimizer** | Adam |

---

### **5️⃣ Model Diagram**  

            [ Input: German Sentence ]  
                        │  
                        ▼  
┌────────────────────────────────────────────┐  
│                ENCODER                     │  
│ Embedding → GRU1 → GRU2 → GRU3 → Context   │  
└────────────────────────────────────────────┘  
                        │  
                        ▼  
┌────────────────────────────────────────────┐  
│                DECODER                     │  
│ Embedding → GRU1 → GRU2 → GRU3 → Dense(Softmax) │  
└────────────────────────────────────────────┘  
                        │  
                        ▼  
            [ Output: English Sentence ]

### **Dataset**
The model is trained on the Europarl dataset, a parallel corpus of German-English sentence pairs.

**Preprocessing Steps**
Tokenization of German and English text
Padding sequences for uniform input length
Adding <start> and <end> tokens


### **📜 License**
This project is open-source and licensed under the MIT License.

### **👨‍💻 Author**
Developed by Ashish Jain
🔗 GitHub: ashish-ai-10