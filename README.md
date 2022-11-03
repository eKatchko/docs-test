GitHub Pages site with MkDocs and MkDocs-Material.  
Configure plugins etc. with mkdocs.yml as usual and known in cloud-user-docs.  
Gather files and assets in docs folder as known in cloud-user-docs.  

GitHub Pages need no initial setting or setup in GitHub. 
They can initially be set up through MkDocs by running `mkdocs gh-deploy`
and updated by a GitHub action (see workflow mkdocs.yml in this repository, need no self-hosted runner).
Updates happen with a push on main branch (e.g. try cloning this repo, adjusting docs/index.md, and pushing it on main, changes
should be visible when both actions ran).
First action (Build and deploy MkDocs) is from this repository to trigger mkdocs deployment, second action (pages-build-deployment) 
is run by a GitHub pages bot (same action that gets triggered when running mkdocs gh-deploy manually).

Local development with 
```shell
python -m venv env
source env/bin/activate
pip install -r mkdocs-requirements.txt
mkdocs serve
```

Suggested workflow:  
We host the docs in a simplevm repository (portal, webapp or a dedicated docs repo).
If someone wants to host their own docs with GitHub Pages, they fork our repository and set it up with the github action.
They would need to keep their fork up to date manually or with a scheduled action (https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows#schedule).  
We would need a fork of our own for staging (because GitHub Pages for a repository can be set up only from one branch).
