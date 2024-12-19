

#  Computer Infrastructure 


**Project Overview:**
This project demonstrates the use of various linux commands (`mkdir, date, wget, touch`) using the command line in the terminal to automate and organize tasks such as creating timestamped files and downloading weather data from an API. A bash script, `weather.sh` is used to automate the process of downloading and storing weather data in timestamped files in a data/weather directory. 

A github actions workflow using a `.yml` file in the `.github/workflows` directory is used to  further automate the execution of the `weather.sh` script. This workflow runs the script daily and commits the downloaded data back to the repository, ensuring the weather data is regularly updated without manual intervention. 

**Github Actions:**
Github actions is a tool provided by github to automate tasks. 
The workflow triggers the execution of the `weather.sh` script and is configured to run daily at a specific time and can be triggered manually or by specific events usch as changes pushed to the naib branch. The workflow is triggered by three events. 
1. push events: runs whenever changes are pushed to the main branch.
2. scheduled events: runs daily at 10:00am (adjusted to 22:00 on 18/12/24)
3. manual triggering: allows manua triggering from the github actions interface via the workflow dispatch. 

The workflow is granted write permissions to the repository enabling it to commit and push the updated weather data back to the repository. 

Workflow steps: 
1. check out the repostitory: uses github/checkout@v3 to clone the repository. The persist-credentials:true ensures the github token is available for git commands such as git push
2.  pull latest changes ensures the local repository is updated with any changes from the remote main branch to avoid conficts. 
3.  set up python allows the workflow to install python 3.x to run dependencies required for this script. 
4. install dependencies: installs necessary python libraries listed in the requirements.txt file to enable API interaction and data processing. 
5. Make weather.sh executable ensures the weather.sh script has executable permissions with chmod+x.
6. run the weather.sh script downloads weather data using wget, processes it and saves the data in a timestamped file in the data/weather directory. 
7. commit and push changes commits the updated weather data and pushes it back to the main branch. 
- git config: sets the github actions bot as the commit author
- git add .: stages all the changes in the repository. 
- git commit: commits changes with a message.
- git push: pushes the changes to the remote repository





**References:**

- https://github.com/ianmcloughlin/2425_computer_infrastructure/blob/main/README.md 
- https://docs.github.com/en/codespaces/overview
- https://docs.github.com/en/actions/about-github-actions/understanding-github-actions
