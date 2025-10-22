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
