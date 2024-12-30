# DL-Project-With-MLOPs

This repository contains a deep learning-based project for image classification with integrated MLOps workflows, containerization, and deployment pipelines. The project uses tools like TensorFlow, DVC, Docker, and CI/CD pipelines for deployment.

---

## Project Structure

- **.dvc**: DVC configurations and cache directory for data versioning.
- **artifacts**: Stores artifacts generated during the training or preprocessing steps.
- **config**: Contains configuration files such as `config.yaml` and `params.yaml`.
- **logs**: Logs for tracking training and pipeline processes.
- **research**: Contains Jupyter notebooks or scripts for exploratory data analysis and model experiments.
- **src**: Core source code for the project:
  - **components**: Contains modular components for preprocessing, training, and evaluation.
  - **pipeline**: Implements the training pipeline logic.
  - **config**: Configuration management utilities.
- **templates**: HTML templates for the web interface.
- **venv**: Virtual environment for Python dependencies.
- **app.py**: Entry point for the web application.
- **main.py**: Main script to orchestrate the training pipeline.
- **dvc.yaml**: DVC pipeline configuration file.
- **requirements.txt**: Lists the Python dependencies.
- **Dockerfile**: Dockerfile for containerizing the application.
- **README.md**: This documentation file.

---

## Workflows

1. Update `config.yaml` for hyperparameters and configurations.
2. Update `params.yaml` for adjustable pipeline parameters.
3. Update entities in the `src` folder.
4. Update the configuration manager in `src/config`.
5. Add or modify components in `src/components`.
6. Define or update pipelines in `src/pipeline`.
7. Modify `main.py` as the central entry point for the pipeline.
8. Update `dvc.yaml` to track and version pipeline stages.

---

## How to Run?

### Step 1: Clone the Repository
```bash
git clone https://github.com/FAbdullah17/DL-Project-With-MLOPs.git
```

### Step 2: Create and Activate Virtual Environment
```bash
conda create -n dlmlops python=3.8 -y
conda activate dlmlops
```

### Step 3: Install Dependencies
```bash
pip install -r requirements.txt
```

### Step 4: Run the Training Pipeline
```bash
python main.py
```

### Step 5: Run the Web Application
```bash
python app.py
```

Visit the local server URL displayed in the terminal to interact with the web app.

---

## DVC Commands

1. Initialize DVC:
   ```bash
   dvc init
   ```

2. Reproduce Pipeline:
   ```bash
   dvc repro
   ```

3. Visualize Pipeline DAG:
   ```bash
   dvc dag
   ```

---

## Deployment with AWS

### AWS Steps:

1. **Create IAM User**:
   - Assign EC2 and ECR full access policies.

2. **Create ECR Repository**:
   - Save the repository URI for future use.

3. **Set Up EC2**:
   - Install Docker on the EC2 instance:
     ```bash
     sudo apt update -y
     sudo apt install docker.io
     ```

4. **Push Docker Image to ECR**:
   - Authenticate and push the image:
     ```bash
     docker build -t <ecr-repo-uri>:latest .
     docker push <ecr-repo-uri>:latest
     ```

5. **Deploy on EC2**:
   - Pull and run the Docker image.

6. **Configure GitHub Secrets**:
   - Add AWS credentials and repository details for CI/CD.

---

## Deployment with Azure

### Azure Steps:

1. Build Docker Image:
   ```bash
   docker build -t <azure-registry-uri>/dlproject:latest .
   ```

2. Push Docker Image to Azure Container Registry:
   ```bash
   docker push <azure-registry-uri>/dlproject:latest
   ```

3. Deploy the Application:
   - Use Azure App Service to pull and run the Docker image.

---

Let me know if you’d like any additional sections or further details!
