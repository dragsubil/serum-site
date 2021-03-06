---
title: The Command-line Program
group: docs
order: 1
---

[Back to the index](%page:docs/index)

# The Command-line Program

Every tasks related to your Serum projects are done by using the Serum
command-line program "`serum`." This document describes all tasks and options
provided by the Serum command-line program.

<blockquote class="note">
  <header>NOTE</header>
  <p>This document assumes that you have installed Serum on an easily reachable
  directory or you have set <code>$PATH</code> environment variable
  appropriately.</p>
</blockquote>

### `init` &mdash; Starts a New Project

```
% serum init [directory]
```

The `init` task initializes a new Serum project into the given `directory`.
If the target directory does not exist, that directory will be automatically
created. If the target directory already exists and is not empty, Serum will
refuse to create a new project. Use `-f (--force)` option to create a new
project anyway.

If the `directory` argument is not passed, Serum will try to initialize a new
project into your current working directory.

#### Options

* `-f` or `--force`<br>
    Forces the initialization of new project on a non-empty directory.

### `build` &mdash; Builds a Project

```
% serum build [-p|--parallel] [(-o|--output) <outdir>] [directory]
```

The `build` task builds your Serum project into a complete website. The
`directory` argument should point at a valid Serum project directory. This
argument may be ignored, in this case you need to be in (i.e, the PWD must be
set to) a valid Serum project directory.

#### Options

* `-p` or `--parallel`<br>
    Basically Serum builds all pages one by one sequentially. If this option
    is provided, Serum will perform a parallel build by launching one build
    process per a page at the same time.
* `-o <outdir>` or `--output <outdir>`<br>
    The output directory of your website can be set by using this option. It
    is recommended to point to an empty directory, because all existing files
    or directories **will be deleted** without any warning or a question. If
    this option is not supplied, Serum will build the website into
    `</path/to/project>/site` directory by default.

    <blockquote class="note">
      <header>NOTE</header>
      <p>Hidden files starting with `'.'` are preserved, as they may contain
      important data, such as Git repository information.</p>
    </blockquote>

### `server` &mdash; The Serum Development Server

```
% serum server [(-p|--port) <port>] [directory]
```

The `server` task builds your Serum project and starts the development server.
Like the `build` task, the optional `directory` option should be a valid Serum
project directory. The website will be built into a temporary directory under
`/tmp`, and will be removed when the server quits.

#### Options

* `-p <port>` or `--port <port>`<br>
    By default, the Serum development server listens on port 8080. If that port
    is unavailable or you need to use the other port, you can override that by
    using this option.

#### Server Commands

Once the development server has successfully started, you can interact with
the server by typing commands. Available commands are:

* `build` &mdash; Rebuilds current project.
* `quit` &mdash; Stops the development server and quit.

<blockquote class="note">
  <header>NOTE</header>
  <p> Please make sure you type the <code>quit</code> command to stop the
  development server. Pressing Control-C causes unclean exit, leaving the
  temporary directory not removed.</p>
</blockquote>

### `help` &mdash; Shows the Help Message

```
% serum help [task]
```

If executed without any argument, the `help` task prints summary of all tasks.
If you want to read detailed explanation about a specific task, give the name of
the task as an argument (e.g. `serum help build`).

## Exit Status

The command-line program reports one of these exit status code depending on the
result of the task:

* `0` &mdash; The task has been completed normally.
* `1` &mdash; An error occurred while running the task.
* `2` &mdash; There is a problem in the command-line argument.
