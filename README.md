# 🧥 Fashion RAG Chatbot (Gemini)

Bu proje, **Akbank GenAI Bootcamp: Yeni Nesil Proje Kampı** kapsamında geliştirilmiş bir **RAG (Retrieval-Augmented Generation)** tabanlı moda danışmanlığı chatbotudur.  
Sistem, **Gemini API** ve **LangChain** kullanarak kullanıcıların giyim tarzı, vücut tipi ve etkinlik bağlamına göre moda önerileri üretmektedir.  
Proje, yapay zekâ tabanlı öneri sistemlerinin gerçek dünyadaki moda danışmanlığına nasıl entegre edilebileceğini göstermektedir.

---

## 🎯 Projenin Amacı
Bu projenin amacı, kullanıcıların kişisel tarz profiline ve bulunduğu ortama uygun **moda kombin önerilerini** yapay zekâ desteğiyle üretmektir.  
Chatbot, RAG mimarisiyle veri tabanında bulunan moda örneklerinden uygun içerikleri çağırır ve Gemini modeliyle anlamlı yanıtlar oluşturur.

---

## 🧵 Veri Seti
- **Kaynak:** [neuralwork/fashion-style-instruct](https://huggingface.co/datasets/neuralwork/fashion-style-instruct)  
- **İçerik:**  
  Veri kümesi, moda alanında kullanıcı profiline göre oluşturulmuş 3 temel alan içerir:
  - `input`: Kullanıcının tarz profili  
  - `context`: Kombin önerisinin yapılacağı durum  
  - `completion`: Yapay zekânın önerisi  
- **İşleme Aşaması:**  
  Her satır `.txt` dosyasına dönüştürülmüş ve ChromaDB’ye aktarılmıştır.  
  Toplam 3193 adet belge oluşturulmuştur.  

Örnek bir kayıt:
USER_PROFILE: Klasik giyim tarzını seven bir kadın
OCCASION: Yaz daveti için kombin önerisi
RECOMMENDATION: İnce askılı midi elbise, hasır çanta ve açık topuklu sandalet önerilir.

---
## ⚙️ Kullanılan Teknolojiler

| Bileşen | Teknoloji |
|----------|------------|
| 💬 LLM Modeli | Google Gemini 2.5 Flash |
| 🔍 Framework | LangChain |
| 🧠 Embedding Model | sentence-transformers/all-MiniLM-L6-v2 |
| 🗂️ Vektör Veritabanı | ChromaDB |
| 💻 Arayüz | Gradio |
| ☁️ Ortam | Google Colab |

---

## 🧩 RAG (Retrieval-Augmented Generation) Mimarisi

Proje, **RAG (Retrieval-Augmented Generation)** mimarisine dayanır.  
Bu mimari sayesinde chatbot, yanıt vermeden önce veri tabanındaki ilgili moda örneklerini geri çağırır.

**Aşamalar:**
1. Kullanıcının sorusu alınır.  
2. Chroma veritabanından en alakalı 4 belge (`k=4`) geri çağrılır.  
3. Bu belgeler “context” olarak Gemini modeline gönderilir.  
4. Gemini, Türkçe ve kısa bir yanıt üretir.  
5. Yanıt, Gradio arayüzünde kullanıcıya gösterilir.

**Mimari Şema:**

```mermaid
graph LR
A[User Question] --> B[Retriever - ChromaDB]
B --> C[Relevant Context]
C --> D[Gemini 2.5 Flash Model]
D --> E[Generated Answer]
E --> F[Gradio UI Output]
```

## 🧠 Elde Edilen Sonuçlar

- Chatbot, kullanıcı girdilerine göre tutarlı ve bağlamsal moda önerileri sunabilmektedir.

- Türkçe dilinde yanıtlar kısa, anlaşılır ve profesyonel bir stil danışmanı üslubuna sahiptir.

- Chroma veritabanı ile hızlı geri çağırma (retrieval) sağlanmıştır.

