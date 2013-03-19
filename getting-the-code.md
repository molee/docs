---
layout: default
title: Getting the code
pygments: true
---

## About the repositories

The entirety of the {{site.project_title}} is composed of a number of Git
repositories. Most are included as submodules in the main toolkitchensink repository.
However, understanding the various pieces will help you navigate the codebase.

#### Polyfill repositories

Each new web platform feature has a corresponding polyfill repository. The primary
goals behind this are two-fold:

1. make the polyfills work across all modern browsers
-  each polyfill can stand on its own and be used à la carte in projects.

#### Platform

[https://github.com/toolkitchen/platform](https://github.com/toolkitchen/platform)

The [platform](https://github.com/toolkitchen/platform) repository references each of the polyfills as submodules, and contains integration tests, loader, and build tools for the amalgamated polyfills.

See [Tooling Strategy](tooling-strategy.html) for information.

#### Toolkit

[https://github.com/toolkitchen/toolkit](https://github.com/toolkitchen/toolkit)

The [toolkit](https://github.com/toolkitchen/toolkit) repository contains the guts
of the project. It pulls in the [platform](https://github.com/toolkitchen/platform)
polyfill repo as a submodule, contains examples, demos, tools, and the [Toolkit kernel](toolkit-kernel-explainer.html).

<p class="alert">
  <strong>Note</strong>: toolkit is in a state of flux. The code in the <em>dev</em>
branch has recently been revamped. In particular, it loads platform as a submodule.
<em>master</em> will soon reflect these changes once things are merged.
</p>

If you want to see the development activity (see [Branching Workflow](branching-strategy.html)), checkout the _dev_ branch directly:

    git clone -b dev https://github.com/toolkitchen/toolkit.git

## Bring on the code!

You can recursively clone and initialize all of its submodules with a single git command.

**To clone toolkitchensink:**

    git clone git://github.com/toolkitchen/toolkitchensink.git --recursive

This creates the following top-level directories in toolkitchensink/,
each a submodule:

-   **toolkit/**—Contains the core Toolkit kernel, a set of components,
    and the platform shims and polyfills.
-   pantry/—Extra components and wrappers for third-party code.
-   projects/—Projects that use, enhance, or demonstrate Toolkit
    technologies.

The toolkit/ folder contains the following sub-folders:

-   **platform/**—Contains the platform shims and polyfills.
-   **components/**— Contains the Toolkit kernel (g-component.html) and
    the initial set of Toolkit components.
-   getting\_started/—A starter project.
-   test/—Test cases.
-   third-party/—Testing libraries.
-   workbench/—Examples of using Toolkit components.

### Test your environment

To check that your development environment is ready, start a local web
server and run one of the included sample projects:

1.  Start a local web server with the **toolkitchensink/** folder as the
    web root.
2.  In a supported browser, go to
    [http://localhost:8000/toolkit/workbench/menu.html](http://localhost:8000/toolkit/workbench/menu.html).
    You should see a menu of items, as shown below.

### Browser requirements

{{site.project_title}} will eventually support all major "evergreen"
(auto-updating) browsers, it currently requires a WebKit-based browser
such as Chrome or Safari.

### Updating {{site.project_title}} submodules

Periodically, we will update the project's submodules on GitHub. To
update your local {{site.project_title}}'s submodules, run the following command
from the toolkitchensink/ folder:

    git submodule update --init --recursive

### About master and dev branches

See [Branching Workflow](branching-strategy.html).
