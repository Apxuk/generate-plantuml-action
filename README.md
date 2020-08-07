# generate-plantuml-action

Generate uml diagrams with Plantuml Server and push them to your repository.

This action ease you to maintain UML.
UML is very useful, but there are some difficulties to maintain.
[PlantUML](https://plantuml.com/) enables you to write UML with text code, that is engineer-friendly so you would like it.

This actions generate UML diagrams from plantuml code
with [PlantUML Server](https://plantuml.com/en/server) when you commit plantUML files
or Markdown files that plantuml code is written in.

PlantUML files must end in either of
- `.pu`
- `.pml`
- `.puml`
- `.plantuml`

Markdown files must end in
- `.md`
- `.markdown`
- `.mdown`
- `.mkdn`
- `.mdwn`
- `.mkd`
- `.mdn`
- `.md.txt`

## Usage

This Action subscribes to Push events.

```workflow
name: generate plantuml
on: push
jobs:
  generate_plantuml:
    runs-on: ubuntu-latest
    name: plantuml
    steps:
    - name: checkout
      uses: actions/checkout@v1
      with:
        fetch-depth: 1
    - name: plantuml
      id: plantuml
      uses: grassedge/generate-plantuml-action@v1.3
      with:
        path: example
        message: "Render PlantUML files"
      env:
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

*input*

- `path` : *required* specify the path to save generated svg files.

*env*

- `GITHUB_TOKEN` : *required* GitHub Token of your repository to commit svg files.

## Demo

see [examples](./example/sample.md) here.

## License

The scripts and documentation in this project are released under the [MIT License](LICENSE).
