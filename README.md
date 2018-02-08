this fork uses [2.1.4 SDK as detailed here](https://github.com/dotnet/core/blob/master/release-notes/releases.csv). It injects a slightly different Procfile which doesn't have any args, but instead runs plain `dotnet mybuildfile` in order to serve the needs of my own project, which was a .NET core 2.0 console app. It also fixes a bug where ${PROJECT_NAME} would resolve to a .csproj file rather than being simply being the bare name without the extension, so I ran `cut -f 1 -d '.'` on PROJECT_NAME and used this on the injected Procfile.

**Please note:** This buildpack is an experimental project and is not officially supported.

# .NET Core Buildpack

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpack) for building [.NET Core](https://www.microsoft.com/net/core) apps using [`.csproj` files](https://docs.microsoft.com/en-us/dotnet/articles/core/tools/project-json).

## Usage

Example usage:

    $ heroku create --buildpack https://github.com/hydrix9/dotnet-buildpack-vs2017.git
    $ git push heroku master

OR
```
    $ heroku buildpacks:set https://github.com/hydrix9/dotnet-buildpack-vs2017
    $ git push heroku master
```

The buildpack will detect your app as .NET Core if it has `.csproj`. If the source code you want to build contains multiple `.csproj` files, you can use a [`.deployment`](https://github.com/projectkudu/kudu/wiki/Customizing-deployments) or set a `$PROJECT` config var to control which one is built.
