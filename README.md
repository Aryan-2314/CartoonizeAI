# 🎨 CartoonizeAI

> Transform your photos and videos into stunning cartoon artwork using deep learning — powered by a White-Box Cartoonization neural network and served via a Flask web application.

![Python](https://img.shields.io/badge/Python-3.7+-blue?style=flat-square&logo=python)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.1.0-orange?style=flat-square&logo=tensorflow)
![Flask](https://img.shields.io/badge/Flask-1.0.2-lightgrey?style=flat-square&logo=flask)
![Docker](https://img.shields.io/badge/Docker-ready-blue?style=flat-square&logo=docker)
![License](https://img.shields.io/badge/License-Apache%202.0-green?style=flat-square)

---

## 📸 Demo

| Original | Cartoonized |
|----------|-------------|
| ![Original](static/sample_images/emma.jpg) | ![Cartoonized](static/sample_images/emma_cartoonized.jpg) |
| ![Original](static/sample_images/cake.jpeg) | ![Cartoonized](static/sample_images/cake_cartoonized.jpeg) |

---

## ✨ Features

- 🖼️ **Image Cartoonization** — Upload any JPG/PNG image and get a cartoon version instantly
- 🎥 **Video Cartoonization** — Process MP4 videos frame-by-frame with audio preserved
- ☁️ **Cloud Integration** — Optional Google Cloud Storage support for scalable deployments
- 🚀 **GPU Acceleration** — Supports CUDA-enabled GPU inference for faster processing
- 🌐 **Colab Compatible** — Run directly in Google Colab via ngrok tunnel
- 🐳 **Dockerized** — One-command deployment with Docker
- ⚙️ **Configurable** — Fine-tune resolution, frame rate, and trimming via `config.yaml`

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| **Backend** | Python 3.7, Flask |
| **ML Framework** | TensorFlow 2.1, TF-Slim |
| **Image Processing** | OpenCV, Pillow, NumPy |
| **Video Processing** | FFmpeg, scikit-video |
| **Cloud Storage** | Google Cloud Storage |
| **Deployment** | Docker, Gunicorn |
| **GPU Inference** | Algorithmia (optional) |

---

## 🚀 Getting Started

### Prerequisites

- Python 3.7+
- `ffmpeg` installed on your system
- (Optional) CUDA 10.1 for GPU support

### Installation

#### Option 1: Virtual Environment (Recommended)

```bash
# 1. Clone the repository
git clone https://github.com/YOUR_USERNAME/cartoonizeAI.git
cd cartoonizeAI

# 2. Create and activate a virtual environment
virtualenv -p python3 venv
source venv/bin/activate        # On Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Configure the app
# Edit config.yaml and set run_local: True for local usage

# 5. Run the app
python app.py
```

Open your browser at `http://127.0.0.1:8080`

#### Option 2: Docker

```bash
docker build -t cartoonize-ai .
docker run -p 8080:8080 cartoonize-ai
```

#### Option 3: Google Colab

Set `colab-mode: True` in `config.yaml`, then run `python app.py`. A public ngrok URL will be generated automatically.

---

## ⚙️ Configuration

Edit `config.yaml` to customize the app behavior:

```yaml
run_local: True          # Set False to use Google Cloud Storage
gpu: False               # Set True if CUDA GPU is available
colab-mode: False        # Set True when running on Google Colab

# Video settings
trim-video: True
trim-video-length: 10    # Max video duration in seconds
original_frame_rate: True
output_frame_rate: 24
original_resolution: False
resize-dim: 480          # Output video width (480p)
```

---

## 📁 Project Structure

```
cartoonizeAI/
├── app.py                          # Main Flask application & routes
├── config.yaml                     # App configuration
├── requirements.txt                # Python dependencies
├── Dockerfile                      # Docker setup
├── gcloud_utils.py                 # Google Cloud Storage utilities
├── video_api.py                    # External GPU video API client
├── white_box_cartoonizer/
│   ├── cartoonize.py               # Core cartoonization logic
│   ├── network.py                  # Neural network architecture
│   ├── guided_filter.py            # Guided filter post-processing
│   └── saved_models/               # Pre-trained model weights
├── static/
│   ├── sample_images/              # Demo images
│   ├── cartoonized_images/         # Output images (generated)
│   └── uploaded_videos/            # Uploaded & processed videos
└── templates/
    └── index_cartoonized.html      # Frontend UI
```

---

## 🧠 How It Works

CartoonizeAI uses the **White-Box Cartoonization** technique, a neural network approach that decomposes images into:

1. **Surface representation** — smoothed textures via guided filtering
2. **Structure representation** — superpixel-based segmentation
3. **Texture representation** — high-frequency texture details

These representations are combined by a trained generator network to produce anime/cartoon-style output, preserving structure while stylizing color and texture.

---

## ☁️ Cloud Deployment (Google Cloud)

To enable cloud mode:

1. Set up a Google Cloud project and enable Cloud Storage
2. Create a service account and download the credentials JSON
3. Set the environment variable:
   ```bash
   export GOOGLE_APPLICATION_CREDENTIALS="/path/to/credentials.json"
   ```
4. Set `run_local: False` in `config.yaml`
5. Update bucket names in `gcloud_utils.py`

---

## 🤝 Contributing

Contributions are welcome! Here's how:

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the **Apache License 2.0** — see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgements

- [White-Box Cartoonization Paper](https://github.com/SystemErrorWang/White-box-Cartoonization) by Xinrui Wang et al.
- [TF-Slim](https://github.com/google-research/tf-slim) for lightweight TensorFlow modeling
- [Flask](https://flask.palletsprojects.com/) for the web framework

---

## 📬 Contact

Made with ❤️ by **Aryan Sharma**

[![GitHub](https://img.shields.io/badge/GitHub-@yourusername-black?style=flat-square&logo=github)](https://github.com/yourusername)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?style=flat-square&logo=linkedin)](https://linkedin.com/in/yourprofile)
