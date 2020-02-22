<h1 align="center">Jellyfin Documentation</h1>
<h3 align="center">Part of the <a href="https://jellyfin.media">Jellyfin Project</a></h3>

This repository houses all documentation for Jellyfin available at [jellyfin.org](https://docs.jellyfin.org/) and written in markdown.

# Layout

Everything is built with [DocFX](https://dotnet.github.io/docfx/) using [DocFX Flavored Markdown](https://dotnet.github.io/docfx/spec/docfx_flavored_markdown.html). See the content section [here](https://dotnet.github.io/docfx/tutorial/docfx_getting_started.html) for a quick tutorial.

## Plugin API

Describe all available API surfaces and class from plugin development.

## ApiSpec

`apispec` is used to overwrite specific plugin API page contexts.

## Docs

`docs` is the main custom documentation directory.
All uids for the custom documentation are relative to this directory, with `administration` and `contributing` shortened to `admin` and `contrib` respectively.
So for example to reference the file `general/administration/installing.md` one would use `xref:admin-installing` with an optional anchor like `xref:admin-installing#arch`.

### Administration

Should be used for documentation related to server setup including non-default configs for more advanced users.

### Contributing

Should be used for documentation related to development, translations, releases, and other ways to contribute to the project.

### Clients

Any documentation related to the clients.

### Server

Any documentation related to managing the server or explaining certain features.

#### Media

Naming conventions for all supported media types, such as movies or podcasts.

#### Plugin

Any plugin documentation.
