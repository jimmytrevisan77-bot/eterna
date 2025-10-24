# Eterna — v0.6 (squelette)

But
Eterna est une application locale tout‑en‑un (SDXL, LLaMA, Coqui XTTS, Whisper). Ce dépôt contient le squelette backend (FastAPI), frontend WPF minimal, scripts d'installation Inno Setup, et fichiers de configuration.

Structure proposée
- backend/: service Python FastAPI (orchestrateur local)
- frontend/: projet WPF (.NET 8, C#)
- installers/: Inno Setup script + helpers
- .github/: CI workflows
- Models, Creations, Logs, Config sont créés sous INSTALL_DIR au runtime

Fichiers initiaux
- AppConfig.json : configuration applicative principale
- Eterna_Path.cfg : fichier stockant INSTALL_DIR

Prérequis (développement)
- Windows 11 recommandé
- Python 3.11
- CUDA 12.4, cuDNN 8.9 (pour accélération GPU)
- PyTorch 2.2.2 (+ torchvision, torchaudio)
- .NET 8 pour le frontend WPF

Installer & Models
- IMPORTANT : LLaMA 3 doit être fourni manuellement par l'utilisateur (non redistribuable). Le downloader intégrera une étape manuelle pour LLaMA.
- SDXL, Coqui XTTS, Whisper, ESRGAN : téléchargés automatiquement via le downloader (ou fournis séparément selon options).

Développement local (backend)
1. Créer et activer un venv Python 3.11
   python -m venv .venv
   .venv\\Scripts\\activate
2. Installer dépendances
   pip install -r backend/requirements.txt
3. Lancer le backend
   uvicorn backend.main:app --host 127.0.0.1 --port 5001 --reload

Prochaines étapes
- Intégrer chargement quantisé LLaMA (GGUF) via chemin manuel
- Intégrer SDXL via diffusers + optimisations
- Finaliser frontend WPF et intégration audio ASIO
