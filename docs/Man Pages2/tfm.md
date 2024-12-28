```
% clamity tfm help
USAGE

	clamity tfm { mystate | apply | vars | smart-import | record-results } [options]
	clamity tfm common { report | update | new-root <state-group> <module-name> }
	clamity tfm settings { show | [un]set aws-profile [profile] }
	clamity tfm cicd complete
	clamity tfm { terraform-cmd-and-args }

TFM COMMANDS

	apply - overload the TF apply sub-command to record results
	cicd - CI/CD processing
	common - verify & sync tf code common to all root modules
	init - overload the TF init sub-command to support access to the state
	mystate - help managing backend state contexts with CI/CD pipeline
	record-results - saves state to STATE.md and output to OUTPUT.json
	settings - set properties for the repo
	smart-import - Assist importing live resources into a root module's state
	state-report - summarize resource deployments by state group
	vars - display terraform environment variables
```
