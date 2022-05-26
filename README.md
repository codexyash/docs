~~NOTOC~~

====== Updating Values.yaml ======

Environment variables for most projects are defined through a kubernetes secret and a values.yaml file. These files often contain credentials or API keys and because of that **cannot** be stored in git. The process of updating these files is a bit more complex because of that.

===== Requirements =====

  * When updating an in-house chart, you need the most up-to-date project files, as older files might result in parts of the deployment being reverted to an earlier version. Leading to a broken application and potential data loss.

===== Steps =====

  - Navigate to the root folder of the project
  - Run ''git pull'' or an equivalent command to ensure you have the most up-to-date 
  - Retrieve the current values.yaml file by running ''helm get values <project> >> values.yaml''
  - Edit the ''values.yaml'' file with your changes
  - Submit your changes by running ''helm update <project> ./helm <project> -f values.yaml %%--%%recreate-pods''

===== Notes =====

  * If the chart being updated is not associated with a project but rather a default helm chart, you should substitute ''./helm'' in step 5 with the repository of the chart. e.g. ''stable/dokuwiki''

===== Related pages =====
