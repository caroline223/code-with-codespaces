# Code with GitHub Codespaces and Visual Studio Code

<!--step0

GitHub Codespaces is a development environment that's hosted in the cloud.

- **Who this is for**: Developers, DevOps Engineers, Engineering Managers, Product Managers
- **What you'll learn**: How to create a codespace, push code from a codespace, select a custom image, and customize a codespace
- **What you'll build**: A codespace with devcontainer.json files, customizations, and personalizations
- **Prerequisites**: None
- **Timing**: This course is four steps long and can be completed in less than an hour

<summary><h2> How to start this course!</h2></summary>
 
1. Above these instructions, click **Use this template**.
2. From the dropdown right-click **Create a new repository** and open the link in a new tab.
![Screen Shot 2023-03-07 at 9 28 54 AM](https://user-images.githubusercontent.com/26442605/223501605-e67051f7-50af-4ae0-a18f-6f733a8b6c62.png)
3. In the new tab, follow the prompts to create a new repository.
   - For owner, choose your personal account or an organization to host the repository.
   - We recommend creating a public repository because private repositories will use [Actions minutes](https://docs.github.com/en/billing/managing-billing-for-github-actions/about-billing-for-github-actions).
   ![Create a new repository](https://user-images.githubusercontent.com/1221423/169618722-406dc508-add4-4074-83f0-c7a7ad87f6f3.png)
4. After your new repository is created, wait about 20 seconds, then refresh the page. Follow the step-by-step instructions in the new repository's README.

endstep0-->


<details id=1 open>
<summary><h2>Step 1: Create your first codespace and push code</h2></summary>

_Welcome to "Develop code using GitHub Codespaces and Visual Studio Code"! :wave:_

**What's the big deal about using a codespace for software development?**  A codespace is a development environment that's hosted in the cloud. You can customize your project for GitHub Codespaces by committing configuration files to your repository (also known as configuration-as-code), which creates a repeatable codespace configuration for all users of your project. Each codespace you create is hosted by GitHub in a Docker container that runs on a virtual machine. You can choose the type of machine you want to use depending on the resources you need.

GitHub offers a range of features to help your development team customize a codespace to reach peak configuration and performance needs. For example, you can:

- Create a codespace from your repository 
- Push code from the codespace to your repository
- Use VS Code to develop code
- Customize the codespace with custom images
- Manage the codespace
   
To begin developing using GitHub Codespaces, you can create a codespace from a template or from any branch or commit in a repository. When you create a codespace from a template, you can start from a blank template or choose a template suitable for the work you're doing.

### :keyboard: Activity: Start a codespace

**We recommend opening another browser tab to work through the following activities so you can keep these instructions open for reference.**

1. Start from the landing page of your repository.
2. Click the green **Code** button located in the middle of the page.
3. Select the **Codespaces** tab in the box that pops up and then click the **Create codespace on main** button.

   **Wait about 2 minutes for the codespace to spin itself up. Note: It's a virtual machine spinning up in the background.**

4. Verify your codespace is running. The browser should contain a VS Code web-based editor and a terminal should be present such as the below:
![codespace1](https://user-images.githubusercontent.com/26442605/207355196-71aab43f-35a9-495b-bcfe-bf3773c2f1b3.png)

### :keyboard: Activity: Push code to your repository from the codespace

1. From inside the codespace in the VS Code explorer window, select the `index.html` file.
2. Replace the **h1** header with the below:
```
<h1>Hello from the codespace!</h1>
```
3. Save the file. Note: The file should autosave.
4. Use the VS Code terminal to commit the file change by entering the following commit message:
```
git commit -a -m "Adding hello from the codespace!"
```
5. Push the changes back to your repository. From the VS Code terminal, enter:
```
git push
```
6. Your code has been pushed to your repository!
7. Switch back to the homepage of your repository and view the `index.html` to verify the new code was pushed to your repository.
	
**Wait about 20 seconds then refresh this page for the next step**
</details>

<details id=2>
<summary><h2>Step 2: Add a custom image to your codespace!</h2></summary>

_Nice work! :tada: You created your first codespace and pushed code using VS Code!_

You can configure the development container for a repository so that any codespace created for that repository will give you a tailored development environment, complete with all the tools and runtimes you need to work on a specific project.

**What are development containers?**  Development containers, or dev containers, are Docker containers that are specifically configured to provide a fully featured development environment. Whenever you work in a codespace, you are using a dev container on a virtual machine.

A dev container file is a JSON file that lets you customize the default image that runs your codespace, VS code settings, run custom code, forward ports and much more!

Let's add a `devcontainer.json` file and add a custom image.
 
### :keyboard: Activity: Add a .devcontainer.json file to customize your codespace

1. Navigating back to your **Code** tab of your repository, click the **Add file** drop-down button, and then click `Create new file`.
2. Type or paste the following in the empty text field prompt to name your file.
```
.devcontainer/devcontainer.json
```
3. In the body of the new **.devcontainer/devcontainer.json** file, add the following content:
```
{
    // Name this configuration
    "name": "Codespace for Skills!",
    // Use the base codespace image
    "image": "mcr.microsoft.com/vscode/devcontainers/universal:latest",
    
    "remoteUser": "codespace",
    "overrideCommand": false
}
```
4. Click **Commit changes** and then select **Commit changes directly to the `main` branch**.
5. Create a new codespace by navigating back to the **Code** tab of your repository.
6. Click the green **Code** button located in the middle of the page.
7. Click the **Codespaces** tab on the box that pops up.
8. Click the **Create codespace on main** button OR click the `+` sign on the tab. This will create a new codespace on the main branch. (Notice your other codespace listed here.)

   **Wait about 2 minutes for the codespace to spin itself up.**

9. Verify that your new codespace is is running, as you did previously.

Note the image being used is the default image provided for GitHub Codespaces. It includes runtimes and tools for Python, Node.js, Docker, and more. See the full list here: https://aka.ms/ghcs-default-image. Your development team can use any custom image that has the necessary prerequisites installed. For more information, see [codespace image](https://aka.ms/configure-codespace). 
	
**Wait about 20 seconds then refresh this page for the next step**

</details>
<details id=3>
	
<summary><h2>Step 3: Customize your codespace!</h2></summary>

_Nice work! :tada: You created a codespace with a custom image!_

You can customize your codespace by adding VS code extensions, adding features, setting host requirements, and much more.
	
Let's customize some settings in the `.devcontainer.json` file!

 ### :keyboard: Activity: Add customizations to the `devcontainer` file

1. Navigate to the `.devcontainer/devcontainer.json` file.
2. Add the following customizations to the body of the file before the last `}`. 
```
    ,    
    // Add the IDs of extensions you want installed when the container is created.
    "customizations": {
        "vscode": {
            "extensions": [
                "GitHub.copilot"
            ]
        },
        "codespaces": {
            "openFiles": [
                "codespace.md"
            ]
        }
    }
```
3. Click **Commit changes** and then select **Commit changes directly to the `main` branch**.
4. Create a new codespace by navigating to the landing page of your repository.
5. Click the **Code** button located in the middle of the page.
6. Click the **Codespaces** tab on the box that pops up.
7. Click the **Create codespace on main** button.

   **Wait about 2 minutes for the codespace to spin itself up.**

8. Verify your codespace is running, as you did previously.
9. The `codespace.md` file should show up in the VS Code editor.
10. The `copilot` extension should show up in the VS Code extension list.
	
This will add a VS Code extension as well as open a file on start up of the codespace.

Next lets add some code to run upon creation of the codespace!

 ### :keyboard: Activity: Execute code upon creation of the codespace

1. Edit the `.devcontainer/devcontainer.json` file.
2. Add the following postCreateCommand to the body of the file before the last `}`. 
```
    ,
    "postCreateCommand": "echo '# Writing code upon codespace creation!'  >> codespace.md"
```
3. Click **Commit changes** and then select **Commit changes directly to the `main` branch**.
4. Create a new codespace by navigating to the landing page of your repository.
5. Click the **Code** button located in the middle of the page.
6. Click the **Codespaces** tab on the box that pops up.
7. Click the **Create codespace on main** button.

   **Wait about 2 minutes for the codespace to spin itself up.**

8. Verify your codespace is running, as you did previously.
9. Verify the `codespace.md` file now has the text `Writing code upon codespace creation!`.
	
**Wait about 20 seconds then refresh this page for the next step.**
 
</details>

<details id=4>
<summary><h2>Step 4: Personalize your codespace!</h2></summary>

_Nicely done customizing your codespace!_ :partying_face:

When using any development environment, customizing the settings and tools to your preferences and workflows is an important step. GitHub Codespaces offers two main ways of personalizing your codespace: `Settings Sync` with VS Code and `dotfiles`.
	
`Dotfiles` will be the focus of this activity.
	
**What are `dotfiles`?**  Dotfiles are files and folders on Unix-like systems starting with . that control the configuration of applications and shells on your system. You can store and manage your dotfiles in a repository on GitHub.

Let's see how this works!

### :keyboard: Activity: Enable a `dotfile` for your codespace

1. Start from the landing page of your repository.
2. In the upper-right corner of any page, click your profile photo, and then click **Settings**.
3. In the **Code, planning, and automation** section of the sidebar, click **Codespaces**.
4. Under **Dotfiles**, select **Automatically install dotfiles** so that GitHub Codespaces automatically installs your dotfiles into every new codespace you create.
5. Click **Select repository** and then choose your current skills working repository as the repository from which to install dotfiles.

### :keyboard: Activity: Add a `dotfile` to your repository and run your codespace
	
1. Start from the landing page of your repository.
2. Click the **Code** button located in the middle of the page.
3. Click the **Codespaces** tab on the box that pops up.
4. Click the **Create codespace on main** button.

   **Wait about 2 minutes for the codespace to spin itself up.**

5. Verify your codespace is running. The browser should contain a VS Code web-based editor and a terminal should be present such as the below:
![codespace1](https://user-images.githubusercontent.com/26442605/207355196-71aab43f-35a9-495b-bcfe-bf3773c2f1b3.png)

1. From inside the codespace in the VS Code explorer window, create a new file `setup.sh`.
2. Add the following code inside of the file:
```
#!/bin/bash

sudo apt-get update
sudo apt-get install sl
```
	
3. Save the file. Note: The file should autosave.
4. Commit the file changes. From the VS Code terminal enter:
```
git add setup.sh --chmod=+x
git commit -m "Adding setup.sh from the codespace!"
```
5. Push the changes back to your repository. From the VS Code terminal, enter:
```
git push
```
6. Switch back to the homepage of your repository and view the `setup.sh` to verify the new code was pushed to your repository.
7. Close the codespace web browser tab.
8. Click the **Create codespace on main** button.

   **Wait about 2 minutes for the codespace to spin itself up.**

9. Verify your codespace is running, as you did previously.
10. Verify the `setup.sh` file is present in your VS Code editor.
11. From the VS Code terminal, type or paste:
```
/usr/games/sl
```
11. Enjoy the show!

</details>

<details id=X>
<summary><h2>Finish</h2></summary>

_Congratulations friend, you've completed this course!_

<img src="https://octodex.github.com/images/welcometocat.png" alt=celebrate width=300 align=right>

Here's a recap of all the tasks you've accomplished in your repository:

* You learned how to create a codespace and push code to your repository from the codespace.
* You learned how to use custom images in your codespace.
* You learned how to customize your codespace.
* You learned how to personalize your codespace.

### Additional learning and resources

- [Developing in a codespace](https://docs.github.com/en/codespaces/developing-in-codespaces/developing-in-a-codespace). Learn how to delete a codespace, open an existing codespace, connect to a private network, forward ports, and much more.
- [Set up your repository](https://docs.github.com/en/codespaces/setting-up-your-project-for-codespaces/introduction-to-dev-containers). Learn how to set minimum machine specs for a codespace, add badges, set up a template repo, and much more.
- [Personalize and customize GitHub Codespaces](https://docs.github.com/en/codespaces/customizing-your-codespace/personalizing-github-codespaces-for-your-account). Learn how to use setting sync for your codespace, add dotfiles, set the default region, set the default editor, and much more.
- [Prebuild your codespace](https://docs.github.com/en/codespaces/prebuilding-your-codespaces/about-github-codespaces-prebuilds)
- [Manage your codespace](https://docs.github.com/en/codespaces/managing-codespaces-for-your-organization/enabling-github-codespaces-for-your-organization)


### What's next?

- Learn more about securing your supply chain by reading: [GitHub Codespaces overview](https://docs.github.com/en/codespaces/overview).
- [We'd love to hear what you thought of this course](https://github.com/skills/.github/discussions).
- [Learn another GitHub skill](https://github.com/skills).
- [Read the Get started with GitHub docs](https://docs.github.com/en/get-started).
- To find projects to contribute to, check out [GitHub Explore](https://github.com/explore).

</details>

---

Get help: [Review the GitHub status page](https://www.githubstatus.com/)

&copy; 2022 GitHub &bull; [Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/code_of_conduct.md) &bull; [MIT License](https://gh.io/mit)
