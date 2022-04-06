# Setup local isolated development environments using Remote Containers

TIL in VSCode you can easily setup a completely isolated development environment using Docker containers. Great way to bootstrap a completely new tech stack without having to bloat your local machine, and also get your teammates up and running in a specific environment.

Easiest way to start playing around with it: 
* Open command palette (`Ctrl+Shift+P`)
* Select "Remote containers: Try a development container sample..."
* Choose one of the samples, e.g. Python
* New VSCode instance starts with a brand new Hello World Flask app, in a container!

For more info see the official repo at https://github.com/microsoft/vscode-dev-containers

In the repo you can find a buuunch of [reusable dev container definitions](https://github.com/microsoft/vscode-dev-containers/tree/main/containers). Rust, .NET, RoR, even whole data science environments with Python and Anaconda.