# MyApp

Welcome to MyApp! This project consists of independent components developed in Go, Next.js (TypeScript), and WordPress. Each component has its own dedicated CI/CD pipeline to ensure quality and efficiency.

## Prerequisites

Before you begin, ensure you have the following installed:

- Dockerhub https://hub.docker.com/repositories/abamrara (docker push abamrara/my-wordpress-site:tagname, docker push abamrara/my-nextjs-app:tagname)
- [Go](https://golang.org/dl/)
- [Node.js](https://nodejs.org/)
- [npm](https://www.npmjs.com/)
- [PHP](https://www.php.net/)
- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Components

### Go Application

The Go application is a simple web server written in Go language.

- **Build the Docker Image:** Navigate to the directory containing the Dockerfile for the Go application and run `docker build -t my-go-app .`.
- **Run the Docker Container:** Once the Docker image is built, run `docker run -d -p 8080:8080 my-go-app`.
- **Access the Application:** Visit `http://localhost:8080` in your web browser.

  ### coding standard enforcement
  - **Linting and Coding Standards:** We use GolangCI-Lint to enforce coding standards for Go.
  - **CI Pipeline Integration:** GolangCI-Lint checks are integrated into the CI pipeline for the Go component.


### Next.js (TypeScript) Application

The Next.js application is a simple frontend written in TypeScript.

- **Build the Docker Image:** Navigate to the directory containing the Dockerfile for the Next.js application and run `docker build -t my-nextjs-app .`.
- **Run the Docker Container:** Once the Docker image is built, run `docker run -d -p 3000:3000 my-nextjs-app`.
- **Access the Application:** Visit `http://localhost:3000` in your web browser.

### coding standard enforcement
   - **Linting and Coding Standards:** We use ESLint and Prettier to enforce coding standards for TypeScript.
   - **CI Pipeline Integration:** ESLint and Prettier checks are integrated into the CI pipeline for the Next.js (TypeScript) component.


### WordPress Application

The WordPress application is a content management system (CMS) written in PHP.

- **Set Up WordPress:** Set up WordPress locally or on a server following the official WordPress installation guide.
- **Configure WordPress:** Configure WordPress by setting up your database, configuring your `wp-config.php` file, and installing any necessary plugins or themes.
- **Deploy WordPress:** Deploy your WordPress application using your preferred hosting platform or server.

  ### coding standard enforcement
  - **Linting and Coding Standards:** We use PHP_CodeSniffer (PHPCS) to enforce WordPress coding standards.
  - **CI Pipeline Integration:** PHPCS checks are integrated into the CI pipeline for the WordPress component.
  - each component of web application enforces coding standards using the appropriate tools (PHPCS for WordPress, GolangCI-Lint for Go, ESLint and Prettier for 
    Next.js with TypeScript) and integrates these checks into their respective CI pipelines. Adjust the configurations and settings as needed based on your 
    project's specific requirements.

## Orchestration:

1. Update Docker Compose File:
Create or Modify Docker Compose File:

2. If you don't have a docker-compose.yml file already, create one in the root directory of your project. If you already have one, open it for modification.
Define Services:

3. Add service definitions for each component (Go, Next.js, WordPress) in the Docker Compose file.
Specify the necessary configurations such as container name, image, ports mapping, environment variables, volumes, etc.
Link Services:

4. Ensure that services are properly linked if they need to communicate with each other.
Network Configuration:

5. Set up networking configurations if services need to communicate over a shared network.
Volumes Configuration:

6. Configure volumes to persist data if required. For example, for the WordPress service, you might want to mount a volume for the WordPress data directory

## To spin up the entire extended application stack locally, follow these steps:

1. **Clone the Repository:**
    git clone <repository-url>
    
2. **Navigate to the Project Directory:**
    cd MyApp
  
3. **Run Docker Compose:**

    Run the following command to start the entire application stack:

    docker-compose up
  

4. **Access the Applications:**

    - Go Application: Visit `http://localhost:8080` in your web browser.
    - Next.js Application: Visit `http://localhost:3000` in your web browser.
    - WordPress Application: Visit `http://localhost:8081` in your web browser.
  
   Create or Modify Docker Compose File:

If you don't have a docker-compose.yml file already, create one in the root directory of your project. If you already have one, open it for modification.
Define Services:

Add service definitions for each component (Go, Next.js, WordPress) in the Docker Compose file.
Specify the necessary configurations such as container name, image, ports mapping, environment variables, volumes, etc.
Link Services:

Ensure that services are properly linked if they need to communicate with each other.
Network Configuration:

Set up networking configurations if services need to communicate over a shared network.
Volumes Configuration:

Configure volumes to persist data if required. For example, for the WordPress service, you might want to mount a volume for the WordPress data directory.


## CI/CD Pipeline Extension:

1. Within each component's CI/CD workflow file, define separate jobs for building, testing, and deploying.
2. Use the needs keyword to ensure that deployment jobs wait for the build jobs to complete successfully before starting.
3. Ensure that deployment steps include commands or scripts to deploy the respective component to the staging environment.
4. Adjust the deployment steps based on your specific deployment targets and procedures.
5. Test the CI/CD pipelines thoroughly to ensure that deployments to the staging environment are triggered automatically upon successful builds.
6. By following these steps, you'll extend your CI/CD pipelines to include deployment stages for the Go, Next.js, and WordPress components, and set up automatic deployment to a staging environment for successful builds.

## Define Deployment Stages:

    -Extend the existing CI/CD pipelines in each component's workflow file (go-ci.yml, nextjs-ci.yml, wordpress-ci.yml) to include deployment stages.
    -Set Up Deployment Targets:

    -Define deployment targets where each component will be deployed. This could be a staging server or environment.
    -Ensure that you have the necessary credentials or access keys to deploy to these targets.
    
Automatic Deployment:
    -Configure the CI pipeline to automatically trigger deployment to the staging environment upon successful builds.


## End
