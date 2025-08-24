# Using Colab with GT GitHub Enterprise

This guide is for students wanting to push their **private** GitHub repository to [GT GitHub Enterprise](https://github.gatech.edu/).

## Instructions

These instructions are provided “as is” without any warranties. Use at your own risk.

I strongly encourage you to understand and test the instructions.

### WARNING: DO NOT USE A PUBLIC GIT REPOSITORY!

These two repositories are public to demonstrate the process. Your schoolwork should **always remain private** in both GitHub and GT GitHub unless otherwise instructed.

- https://github.com/murphyjt/colab-example
- https://github.gatech.edu/jmurphy312/colab-example

## Connect Colab to GitHub

Make sure to Sign in to Colab with your Google account.

If you haven't already, you can authorize Colab to access your GitHub by selecting **File | Save a copy in GitHub**. You will be prompted to "Sign in to GitHub to continue to Colaboratory". Sign in and authorize. You can now open notebooks and commit notebooks to your GitHub.

## Opening a GitHub notebook in Colab

If you already have a notebook in a repo, select **File | Open notebook**, click GitHub and with **Include private repos** checked, find your repo and branch and select the notebook you want to open.

## Saving a notebook in Drive to GitHub

Ensure you have a GitHub repo set up and that it has at least one branch-if you're creating a new repo in GitHub, you can include a README to ensure a main branch is created.

With a repo and branch in mind, open your Google Drive notebook and then select **File | Save a copy in GitHub**. In the modal, find your repository and branch, change the File path if needed, and add a Commit message. Click OK when you're ready to commit and push. Follow the next steps to finish setting up.

Now select **File | Open notebook** and open the notebook you just saved to GitHub. Now when you select **File** you'll see the new command **View on GitHub** and more importantly you'll see **Save** and **Revision history**. It's safe to click **Save**; if you do you'll see a modal with the Repository, Branch and File path pre-filled and the option to add a Commit message. If you click OK you're creating a new commit and it will be pushed to your GitHub.

**Warning:** If two people (or two machines) edit the same notebook in GitHub at the same time, merge conflicts can occur. As far as I know, Colab does not have a built-in merge conflict resolution tool. You will need to pull the repo locally and use git merge or a merge tool (e.g., VS Code, GitHub Desktop) to manually resolve conflicts.

## Syncing GitHub with GT GitHub Enterprise

Clone your GitHub repository. To keep it simple, we'll use HTTPS. When using HTTPS you might need to enter your Username and Password when prompted.

```sh
# You can clone this repo if you're just testing out the process
$ git clone https://github.com/murphyjt/colab-example.git
```

After your repository is cloned, `cd` into it and add a new remote. If you haven't already, [create a repository](https://github.gatech.edu/new) on GT GitHub; the repository names don't need to match. I've named this remote **gatech**.

```sh
# Your URL will look like https://github.gatech.edu/<username>/<repo>.git
$ git remote add gatech https://github.gatech.edu/jmurphy312/colab-example.git
```

You can list remotes anytime with `git remote -v`.

With your remote added, the only remaining step is to push your repo's branch to it. This command will push your `main` branch to the remote `gatech`.

```sh
$ git push gatech main
```

You're done! Your commits for the `main` branch (or any other branch you push) is now in your GT GitHub repository.

## Windows

Install [Git for Windows](https://gitforwindows.org/). Include Git Credential Manager in the installation.

### Using HTTPS

When using HTTPS, you might be prompted by the Git Credential Manager. This should be used when on Windows.

### Using SSH

To use SSH on Windows, you'll want to enable `ssh-agent` and add your private key.

```powershell
PS C:\Users\murphyjt> Get-Service ssh-agent | Set-Service -StartupType Automatic
PS C:\Users\murphyjt> Start-Service ssh-agent
PS C:\Users\murphyjt> Get-Service ssh-agent
```

```powershell
PS C:\Users\murphyjt> ssh-add $env:USERPROFILE\.ssh\id_gatech
```

This section is incomplete.

## Disclaimer

THE SOFTWARE AND DOCUMENTATION ARE PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE, TITLE, AND NON-INFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES, OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT, OR OTHERWISE, ARISING FROM, OUT OF, OR IN CONNECTION WITH THE SOFTWARE, DOCUMENTATION, OR THE USE OR OTHER DEALINGS IN THEM.