# PawFinder
MLOPs - a lightweight computer-vision service that identifies the breed of a cat or dog from a single photo

## Project statement

Build and production-ize a lightweight computer-vision service that identifies the breed of a cat or dog from a single photo.
Using the Oxford-IIIT Pet Dataset, I will fine-tune a pre-trained CNN, wrap the model in a FastAPI micro-service, orchestrate the training pipeline with Prefect, track experiments in MLflow, provision all cloud resources with Terraform, containerise with Docker, and monitor prediction quality with Evidently. The finished repo and README will satisfy every rubric item of the course's end-to-end ML project.

## 50-hour game plan

| Day / hrs                   | Deliverable                  | Key tasks & tips                                                                                                                                                                    |
| --------------------------- | ---------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Kick-off (3 h)**          | Repo scaffold                | • Init GitHub repo, MIT License<br>• README skeleton & architecture diagram placeholder                                                                                             |
| **Data & baseline (6 h)**   | Working notebook             | • Install `torch` / `torchvision` in Colab<br>• Download Oxford-IIIT Pet (≈ 800 MB)<br>• Build `DataLoader`<br>• Fine-tune MobileNetV2 → \~80 % val acc<br>• Log runs to **MLflow** |
| **Model registry (4 h)**    | Best model saved             | • `mlflow.register_model` top run<br>• Pickle preprocessing transforms                                                                                                              |
| **Pipeline refactor (6 h)** | Prefect flow                 | • Flow = *download → preprocess → train → eval → register*<br>• Parametrize epochs, LR                                                                                              |
| **IaC + cloud (5 h)**       | GCP VM + bucket              | • Minimal **Terraform** for an `n1-standard-4` GPU VM & GCS bucket                                                                                                                  |
| **Containerisation (4 h)**  | `Dockerfile`                 | • Multi-stage build<br>• `make test` & `make lint` targets                                                                                                                          |
| **API service (5 h)**       | FastAPI app                  | • `POST /predict` multipart image → breed & confidence JSON                                                                                                                         |
| **CI/CD (4 h)**             | GitHub Actions               | • Lint (ruff) & tests (pytest)<br>• Build & push image to GHCR                                                                                                                      |
| **Monitoring (5 h)**        | Evidently report             | • Weekly batch score 200 fresh images<br>• Prefect alert if accuracy < threshold                                                                                                    |
| **Docs & video (4 h)**      | Polished README + 2-min demo | • Architecture diagram<br>• Usage instructions                                                                                                                                      |
| **Buffer / polish (4 h)**   | Point-grabbers               | • Pre-commit hooks<br>• Integration test: `curl -F "file=@sample.jpg" /predict`                                                                                                     |
