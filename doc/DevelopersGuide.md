# Pip.WebUI Developer's Guide

This is the master project for all Pip.WebUI modules. Its purpose to provide easy-to-use development environment
and simplify dependency management across modules. Although it is optional, it is highly recommended to use it.

## <a name="contents"></a> Contents

* [Installing](#install)
* [Developing](#develop)
* [Building](#build)
* [Testing](#test)
* [Releasing](#release)
* [Contributing](#contrib)

## <a name="install"></a> Installing

1\. - Download and install Node.js from https://nodejs.org/en/download/

2\. - Install the Angular CLI globally.

```bash
npm install -g @angular/cli
```

3\. Clone the project from github repository (for example layouts).

```bash
git clone https://github.com/pip-webui2/pip-webui2-layouts.git
```

4\. Initialize the project

Install npm dependencies:
```bash
npm install
```

Serve examples of specific module:
```bash
ng serve --open
```

## <a name="develop"></a> Developing

### Check in / push changes

The development is done as usual under specific modules. But when you commit, you shall do it twice: 
commit and push changes in the submodule you worked on, then commit and push changes from the master project.

```bash
cd <submodule>
git add -A .
git commit -am "You message"
git push

cd ..
git commit -am "You message"
git push
```

To simplify commits you can use gulp task in the master project:
```bash
gulp checkin -m "Your message"
```

### Check out / pull changes

To pull all submodules in one command run the following gulp task from the master project:
```bash
gulp pull
```

### Known issues

- Visual Studio Code, and, possibly, other IDEs periodically call git to check its status. That creates lock file in **.git** folder and cause 'gulp pull' and 'gulp checkin' commands to fail. To avoid that close your IDE and repeat the command.

- Sometimes submodules switch to detach mode and push fails. To fix that do:
```bash
cd <detauched submodule>
git checkout origin master
git pull
```

## <a name="build"></a> Building

Build source code across all submodules. It will automatically check for errors. If any error found the build will fail.
```
ng build
```

## <a name="test"></a> Testing

Execute unit tests in all submodules:
```bash
ng test
```

Check for errors in coding style in all submodules:
```bash
ng lint
```

<## <a name="releasing"></a> Releasing

1\. Prepare module for release. Check and update **CHANGELOG.md** files.

2\. Change version number in **package.json**.

4\. Publish release to the global NPM repository.

Remember: to publish to NPM you must have proper permissions from the team.
```bash
npm login
npm publish ./
```

## <a name="contrib"></a> Contributing

For those who would like to contribute to the project as external contributor or become a part of Pip.WebUI team, 
please, read [Contributor's Guide](https://github.com/pip-webui/pip-webui/blob/master/doc/ContributorsGuide.md).
