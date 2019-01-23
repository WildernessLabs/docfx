
# DocFX Site

For instructions on how to use DocFX, visit https://dotnet.github.io/docfx/

## Getting Started

1. Install DocFX
  
  On OSX ([brew](https://brew.sh/) required)
  ```
  brew install docfx
  ```
  On Windows ([chocolately](https://chocolatey.org/docs/installation) required)
  ```
  choco install docfx -y
  ```

2. Clone Repo  

If you haven't cloned [Meadow.Core](https://github.com/WildernessLabs/Meadow.Core) and [Meadow.Foundation](https://github.com/WildernessLabs/Meadow.Foundation) do so first and then clone `docfx` as a sibling. 

  ```
  git clone git@github.com:WildernessLabs/Meadow.Core.git
  ```

3. Launch site:
  
  ```
  cd docfx
  docfx docfx.json --serve
  ```

### Configuring Scripts First Time

To make the helper scripts executable, run these commands in the terminal after cloning:

```
chmod +x ./build-serve-docs.sh
chmod +x ./build-docs.sh
chmod +x ./get-latest.sh
```

## Committing Changes

Before committing back to the repo, run `./build-docs.sh`. This will ensure you have the latest from  `Meadow.Core` and `Meadow.Foundation` repos.  Here's a breakdown of helper scripts:  
- `./build-docs.sh` - runs `./get-latest.sh`, then runs `docfx docfx.json`       
- `./build-serve-docs.sh` - runs `./get-latest.sh`, then runs `docfx docfx.json --serve`  
- `./get-latest.sh` - gets latest from `Meadow.Core` and `Meadow.Foundation`

## DocFX stuff

You can link to APIs this way:

* MD link notation: `[IApp](xref:Meadow.IApp)`
* `@` notation: `@"Meadow.IApp"`

Both will resolve at build time to the `Meadow.IApp` api doc entry.

The `@` notation is shorter, but the MD notation allows you to set the link title.

## Troubleshooting

If it fails on Mac/Linux with some `SQLitePCLRaw` nonsense, run this:

```
nuget install -OutputDirectory $TMPDIR SQLitePCLRaw.core -ExcludeVersion
for docfx in /usr/local/Cellar/docfx/*; do cp "$TMPDIR/SQLitePCLRaw.core/lib/net45/SQLitePCLRaw.core.dll" "$docfx/libexec"; done
```