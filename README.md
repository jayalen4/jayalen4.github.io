# Roanoke Park Elms - call-to-action

Simple static site to fundraise for the Roanoke Park Elms.

This readme includes a tutorial for creating a dev environment using GitHub Codespaces

## Setting up a Codespace for Development

Start by navigating to the code repository. If you're already here, you can click the Code button:

![Click code](./assets-readme/Screenshot%202025-05-21%20at%2007.22.38.png)

Click "Create Codespace"

![Click create codespace](./assets-readme/Screenshot%202025-05-21%20at%2007.24.34.png)

A new tab/window opens where the Codespace is being created.

Just a heads up this step will probably fail. While it is probably possible to fix this, if it fails for the same reason it did for you that it does for me, then running the static site will still work...
![heads up on failed postCreateStep](./assets-readme/Screenshot%202025-05-21%20at%2007.27.31.png)

Click the `Terminal` tab to open the terminal

![Click Terminal tab](./assets-readme/Screenshot%202025-05-21%20at%2007.29.06.png)

Click the plus on the right side tab to open a new Terminal

![Click Terminal tab](./assets-readme/Screenshot%202025-05-21%20at%2007.29.48.png)


This is the command you need to run inside the Terminal to start the server:

```bash
bundle exec jekyll serve --force-polling
```

Copy and paste it to the terminal. Accept this prompt if it shows up:

![accept clipboard access prompt](./assets-readme/Screenshot%202025-05-21%20at%2007.30.55.png)

It should look like this. Press Enter to execute the command

![start the server](./assets-readme/Screenshot%202025-05-21%20at%2007.32.16.png)

A port will be opened that you can access the live reloading website on.

*I recommend opening this in a new tab and then making it a separate window*. When you make changes to the code, they will appear on the reloading server!

![open the tab](./assets-readme/Screenshot%202025-05-21%20at%2007.32.32.png)

If you don't see the pop up or need to open it again, click the `Ports` tab and then the globe icon 🌐

![open the tab from ports](./assets-readme/Screenshot%202025-05-21%20at%2007.40.22.png)

> [!NOTE]
> You might receive an "Error forwarding port" - please reload the page! If the problem persists, there actually is probably a problem.

![incorrect port forwarding error](./assets-readme/Screenshot%202025-05-21%20at%2007.40.02.png)

![website loads from dev server](./assets-readme/Screenshot%202025-05-21%20at%2007.40.08.png)

The main files you will likely want to edit are `index.md` and `learn-more.md`. They can be located in the sidebar, edited, saved, and you can reload the site to see how the changes appear ✨

![files to edit](./assets-readme/Screenshot%202025-05-21%20at%2007.48.12.png)

>[!WARNING]
> Once you have finished developing, turn your codespace off as it will continue running otherwise. You can do this from the code repository page in the beginning:
![turn off codespace](./assets-readme/Screenshot%202025-05-21%20at%2007.52.34.png)