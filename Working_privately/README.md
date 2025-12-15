## Working privately (optional)

**This is not needed, and honestly more hastle than it's worth** but if you're nervous about have your learning experience be public record, there's a work around. You can't simply set the Visibility = Private your forked copy of a public repo, but you can create a mirror of the repo and then an independent private repo of your own, and push your mirrored version into that private repo of yours:

*Note: This example assumes you have an SSH key configured but if you don't you can follow those instructions in the Bioinformatics_Onboarding/README.md or GitHub's SSH key guide before continuing.*

1. Mirror-clone the public repo (creates a bare/mirror directory named `My_Onboarding`):
```bash
git clone --mirror git@github.com:karlgrieshop/Bioinformatics_Onboarding.git My_Onboarding
```

2. Create a new *private* repository on GitHub (via the web UI or `gh`). For example, create a repo named `My_Onboarding` in your account and set Visibility = Private.

3. Push the mirror to your new private repository:
```bash
cd My_Onboarding
git push --mirror git@github.com:YOUR_USERNAME/My_Onboarding.git
```

Important notes
- The private mirror is an independent repository and will NOT be part of GitHub's fork network. That means your private copy will sync with the upstream changes to the public Bioinformatics_Onboarding repo, and 
you cannot open a normal pull request from your private repo directly to the public upstream.
- To fetch updates from the original public repo later, clone a normal working copy from your private repo and add the public repo as `upstream` (but as far down the rabbit hole as I go, so you'll have to Google or Copilot your way through that).