this fork uses [2.1.4 SDK as detailed here](https://github.com/dotnet/core/blob/master/release-notes/releases.csv)

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
