# XTC Simple Hello World App using the XDK repository

This is a small project, generated from the "xtc-template-app" GitHub template.
This shows how to run the hello world project in the template app, but instead of
using artifacts from the GitHub Maven Repo for XtcLang, your local Maven repository,
or mavenCentral and gradlePluginPortal (once we have releases publishing there),
to substitute that artifact with an XVM repository.

This may be an easier use case to work from, if you are after the XVM developer
experience, with a small easy-to-understand debuggable application.

To set up this project, you need to clone out the XVM repo somewhere onto
your local hard drive, and set the environment variable XVM_REPO_ROOT to
its absolute path. Then import this project into IntelliJ or your other
favourite IDE, and the rest should be taken care of.

The idea is that you should see both your repository with your simple
HelloWorld XTC project, as well as the XVM code, where every artifact referenced
from the hello world project (as in the template) remains the same, but
is replaced by an includedBuild, so that you can actually modify the XVM
repo, rebuild the project, which should incrementally only rebuild any
artifacts whose code you have changed, and then substitute the references
to said artifacts with the modified XVM code on your local machine.

TODO: This does not work yet, but will soon.

Example:

git clone git@github.com:xtclang/xvm.git $HOME/src/xvm
export XVM_REPO_ROOT=$HOME/src/xvm
./gradlew greet

TODO:
An alterantive way to do this would be to just add XVM as a submodule to this repo,
but git submodules are evil, and I don't trust it not to turn into some kind of
strange hell for the dev team. However, if you think you can do this in an
architecturally sound way, pleae go ahead.

When cloning use --recurse-submodules, or if you forgot git submodule update --init --recursive

--
To pull in upstram changes to xvm:
   git fetch
   git rebase origin/master

   (if you run git diff --submodule you can see the submodule was updated)
   (for logging: git config --global diff.submodule log)

Or:
  git submodule update --remote xvm

@see https://git-scm.com/book/en/v2/Git-Tools-Submodules