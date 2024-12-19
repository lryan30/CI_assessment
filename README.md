


#  Computer Infrastructure 


<img src='https://t3.ftcdn.net/jpg/06/39/62/90/360_F_639629017_YjfnLtEGhYsnXr9GlyXf6dXwLVmVdaRW.jpg'>


***

**Project Overview:**

This project uses linux commands to automate and organise tasks such as creating timestamped files and downloading weather data via an API. A bash script is used to download and save the weather data in timestamped files within an assigned directory. 
Additionally, a Github Actions workflow further automates the execution of the script. This workflow runs the script daily and commits the updated data back to the repository, ensuring the weather data is regularly updated without manual intervention. The project was developed and run in Github Codespaces, a cloud based integrated development environment provided by Github. It allows users to create, edit and run code directly in the cloud. 

***
**Github Actions:**

Github Actions is a continuous integration and continuous delivery (CI/CD) platform integrated directly into Github that automates tasks. In this project, the Github Actions workflow, located in the `.github/workflows` directory  automates the execution of the `weather.sh` script. it runs daily at 10:00am UTC (adjusted to 22:00 on 18/12/24)  but can also be triggered manually or by events like pushes to main branch. The workflow has write permissionsn enabling it to commit and push updated weather data back to the repository. 

Workflow steps: 
-   Check out repository: Clones the repository using `github/checkout@v3` with `persist-credentials:true` for git commands.
-    Pull latest changes: Updates the local repository with any changes from the remote main branch to avoid conficts. 
-   Set up python: Installs python 3.x to run dependencies required for the script. 
-   Install dependencies: Installs libraries listed in the requirements.txt file to enable API interaction and data processing.
 -   Make `weather.sh` executable: Ensures the `weather.sh` script has executable permissions with chmod+x.
-    Run the `weather.sh` script: Downloads weather data and saves as a timestamped file in `data/weather`.
-  Commit and push changes: commits the updated weather data and pushes it to the repository with the following git commands.  
    - git config: sets the github actions bot as the commit author.
    - git add .: stages changes.
    - git commit: commits changes.
    - git push: pushes updates to the repository





**References:**

- https://github.com/ianmcloughlin/2425_computer_infrastructure/blob/main/README.md 
- https://docs.github.com/en/codespaces/overview
- https://docs.github.com/en/actions/about-github-actions/understanding-github-actions
