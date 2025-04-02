# SIT323 5.2D - Deployment of a Dockerised Microservice to Google Cloud Artifact Registry

This project is part of the SIT323 Cloud Native Application Development course. In this assignment, I deployed the Dockerised microservice built in Assignment 5.1P to a private container registry on Google Cloud (using Artifact Registry). I then verified that the published image can be pulled and run successfully.

## 📂 Repository

The code and documentation are hosted on GitHub:  
[https://github.com/my-username/sit323-2025-prac5d](https://github.com/my-username/sit323-2025-prac5d)

## 🛠️ Project Setup

### Step 1: Create and Initialize the GitHub Repository
- Create a new GitHub repository named **sit323-2025-prac5d**.
- Clone the repository locally.
- Navigate to the project directory.

### Step 2: Tag My Docker Image for Artifact Registry
Since this assignment uses Artifact Registry, tag the image with my Artifact Registry address. 
```bash
docker tag calculator:latest us-central1-docker.pkg.dev/sit323-25t1-yuwei-zhu-10a9433/calculator-repo/calculator:latest
```

### Step 3: Authenticate Docker with Artifact Registry
Authenticate Docker using the Google Cloud SDK:
```bash
gcloud auth print-access-token | docker login -u oauth2accesstoken --password-stdin us-central1-docker.pkg.dev
```
This command uses my Google Cloud credentials to enable Docker to push and pull images from Artifact Registry.

### Step 4: Push the Docker Image to Artifact Registry
Push the tagged image to my Artifact Registry repository:
```bash
docker push us-central1-docker.pkg.dev/sit323-25t1-yuwei-zhu-10a9433/calculator-repo/calculator:latest
```

### Step 5: Verify the Published Image
Test that the image can be pulled and run correctly:
```bash
docker run -d -p 3323:3323 us-central1-docker.pkg.dev/sit323-25t1-yuwei-zhu-10a9433/calculator-repo/calculator:latest
```
- `-d` runs the container in the background.
- `-p 3323:3323` maps the container's port 3323 to my local port 3323.

### Step 8: Push the Code and Documentation to GitHub
Commit all changes and push them to my GitHub repository:
```bash
git add .
git commit -m "Deploy Docker image to Artifact Registry and add deployment instructions"
git push origin main
```

## 💻 Usage

1. **Start the Docker Container:**  
   Run the following command to start the container:
   ```bash
   docker run -d -p 3323:3323 us-central1-docker.pkg.dev/sit323-25t1-yuwei-zhu-10a9433/calculator-repo/calculator:latest
   ```

2. **Test the Application:**  
   Open my browser and navigate to `http://localhost:3323` to interact with the microservice.

## 📕 Conclusion

This project demonstrates the process of deploying a Dockerised microservice to Google Cloud Artifact Registry. The key steps include:
- Tagging the Docker image appropriately.
- Authenticating Docker with Artifact Registry.
- Pushing the image to the registry.
- Verifying that the image runs correctly.
- Documenting the process and code in a GitHub repository.
