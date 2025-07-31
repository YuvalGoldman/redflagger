# 🚩 REDFLAGGER – Detecting Sensitive Military Content on Social Media

> **Final Project – Data Science & AI Certification (July 2025)**  
> By: Yuval Goldman, Elad Josef, Boris Soultanovich

---

## 🧭 Why We Built REDFLAGGER

In today’s digital age, every photo, story, or tagged location shared online by soldiers can unintentionally leak sensitive information. A simple selfie in uniform, a visible unit insignia, or even a background sign can compromise operational security (OPSEC).
Social media intelligence (SOCMINT) has been proven effective in real-world threats — from the 2018 NATO experiment using $60 to locate soldiers, to the 2023 exposure of Russian units via a single VK post.
Despite the risks, there is no automated system in place to detect and flag these posts before the damage is done.

---

## 🎯 Project Objective

REDFLAGGER is a **multimodal AI-based decision-support system** that identifies potentially sensitive content shared by military personnel on platforms like Instagram.
The system scans posts, detects military objects in images, analyzes captions, and provides an automated **risk score** for each post — helping organizations flag high-risk cases in real-time.

---

## 🧠 Technologies Used

| Tool/Library           | Purpose |
|------------------------|---------|
| YOLOv8                 | Real-time object detection (e.g., weapons, vests, insignia) |
| Roboflow PRO           | Dataset creation, annotation, augmentation |
| Hugging Face + OpenRouter | NLP-based analysis of captions, risk scoring with LLM |
| OpenCV                 | Image processing and visual masking |
| FastAPI                | Backend service for model handling |
| YAML Rules Engine      | Custom risk scoring logic based on detections |
| Streamlit              | Internal UI for risk evaluation |
| Docker                 | Containerized deployment |
| Notion                 | Task tracking and team documentation |

---

## 📈 Performance Highlights

Over 22 iterations of model tuning, we improved precision and recall significantly:

| Metric        | Initial Value | Final (V22) |
|---------------|---------------|-------------|
| mAP@50        | 0.74          | **0.896**   |
| Precision     | ~0.73         | **0.874**   |
| Recall        | ~0.69         | **0.843**   |
| Labeled images | ~1000        | **3274**    |

We used manual tagging for 2,066 items and created 25 distinct object classes (e.g., M16, Negev, Radome, Vest).

To reduce class confusion (e.g., between M16 and Negev), we:
- Added image augmentations (rotation, blur, lighting)
- Merged semantically similar classes (e.g., radome + Iron Dome)
- Upgraded model from fast → medium variant to improve accuracy (tradeoff accepted)

---

## 🚧 Key Challenges & What We Learned

- **Data scarcity**: Many sensitive object classes were rare. We created and tagged our own dataset.
- **Label confusion**: We used confusion matrices to analyze class-level performance and guide refinements.
- **Defining "sensitive"**: We built a flexible, rules-based + LLM-assisted scoring system.
- **Multimodal integration**: Aligning object detections with caption analysis proved complex — but powerful.
- **Team coordination**: We managed a full MLOps pipeline as a 3-person team.

---

## 👁️ System Flow

1. **Scraping**: Automatically scrapes open Instagram profiles using keyword filters (e.g., #צה״ל, #בסיס).
2. **Image detection**: Detects equipment, uniforms, and locations via YOLOv8.
3. **Caption analysis**: NLP pipeline identifies sensitive text, cross-checks with image.
4. **Risk scoring**: Assigns a score based on object count, type, text match, and context.
5. **Dashboard**: Outputs flagged posts with risk level, explanations, and exportable metadata (e.g., JSON).

---

## 👁️ Visual Demo (Blurred for OPSEC Compliance)

<div align="center">
  <img src="demo/blurred_post1.jpg" width="400"/>
  <img src="demo/blurred_post2.jpg" width="400"/>
</div>

🛡️ All images are anonymized and blurred. No real identities or unit names are shown.

---

## 🔐 Responsible AI & Ethics

- ❌ No real user data or faces shared  
- ❌ No code published (risk of misuse)  
- ✅ AI used for **supporting decisions**, not replacing human judgment  
- ✅ Compliant with OPSEC and data privacy best practices

---

## 🧠 Use Cases & Future Directions

### Potential Use Cases:
- Automated monitoring of soldiers' social media content  
- Risk flagging for cybersecurity or OPSEC units  
- Integration into military social media education programs

### Future Development:
- Expand dataset with international military imagery  
- Add face recognition module for cross-matching units  
- Extend platform support to TikTok, LinkedIn, Facebook  
- Deploy on-premise with secure APIs

---

## 📚 Reference

- [NATO Social Media & Armed Forces Framework (2018)](https://stratcomcoe.org/cuploads/pfiles/nato_framework_for_armed_forces_web_09mar.pdf)

---

## 📫 Contact

**Yuval Goldman**  
[LinkedIn](https://www.linkedin.com/in/yuval-goldman-1a6920204)

---

## 📝 Notes

This project was developed as part of a professional Data Science program.  
For ethical and security reasons, **no source code or real identities** are included.  
For collaboration or demonstration requests, feel free to reach out directly.
