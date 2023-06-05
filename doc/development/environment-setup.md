# **Environment Setup**

## **Table of Contents**

- [**Environment Setup**](#environment-setup)
   - [**Table of Contents**](#table-of-contents)
   - [**VSCode**](#vscode)
      - [**Extensions**](#extensions)
      - [**Workspace Configuration**](#workspace-configuration)
   - [](#)

## **VSCode**

All our projects utilize the power of VSCode, and come with their own IDE configurations (found ind the `.vscode` directory).

### **Extensions**

Our projects use some necessary VSCode extensions, for which you will have pre-generated settings files. Install each of them:

- [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker "Visit") (`cspell`)
- [YAML](https://marketplace.visualstudio.com/items?redhat.vscode-yaml "Visit")
- [ESLint](https://marketplace.visualstudio.com/items?dbaeumer.vscode-eslint "Visit") static code analyzer (`eslint`)
- [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode "Visit") code formatter (`prettier`)
- [Task Explorer](https://marketplace.visualstudio.com/items?itemName=spmeesseman.vscode-taskexplorer "Visit")

> _When opening the monorepo in VSCode, the IDE will suggest these extensions, since they are listed in `.vscode/extensions.json`._

> _For information on our Code Quality Tools, visit the dedicated [development page](./code-quality-tools.md "Visit") discussing the topic in detail._

### **Workspace Configuration**

Open the newly cloned folder in VSCode:

```shell
$ cd <project-folder>
$ code .
```

Be sure, to **save the folder as a VSCode workspace** (`File` > `Save Workspace As`), this way the settings in the `.vscode/settings.json` file that can not be applied on the folder level will be applied on the workspace level of your project (you can ensure this by opening up the newly generated `.code-workspace` JSON file in the IDE). Also, the developer Chrome profile VSCode starts your visuals in will be tied to this workspace (including profile settings, cookies, and passwords).

> _If you're using the new monorepo approach, you will only have to do this step once, but since by default the root of your workspace will be the directory you cloned the monorepo to, you will only access tasks associated with this root level setup. To come over this, we can utilize multi-root workspaces in VSCode, so if you're working on specific visual, you can add it's internal directory to your workspace folders in the IDE (`File` > `Add Folder to Workspace`), and from that on the tasks associated with this directory will show up in your task list too._

##

---

_©2020-2023 Barnabas Bucsy - All rights reserved._
