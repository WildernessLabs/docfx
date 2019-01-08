
# DocFX Site

For instructions on how to use DocFX, visit https://dotnet.github.io/docfx/

## Getting Started

1. Install DocFX
  
  ```
  # OSX, [brew](https://brew.sh/) required
  brew install docfx

  # Windows, [chocolately](https://chocolatey.org/docs/installation) required
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
  
## Troubleshooting

If it fails on Mac/Linux with some `SQLitePCLRaw` nonsense, run this:

```
nuget install -OutputDirectory $TMPDIR SQLitePCLRaw.core -ExcludeVersion
for docfx in /usr/local/Cellar/docfx/*; do cp "$TMPDIR/SQLitePCLRaw.core/lib/net45/SQLitePCLRaw.core.dll" "$docfx/libexec"; done
```