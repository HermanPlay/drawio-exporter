# Draw.io Exporter GitHub Action

A GitHub Action that exports Draw.io (.drawio) diagrams to various formats including SVG, PNG, PDF, JPG, and XML.

## Features

- 🚀 Export Draw.io files to multiple formats (SVG, PNG, PDF, JPG, XML)
- 📁 Outputs the generated file path for use in subsequent workflow steps
- 🐳 Uses the reliable `rlespinasse/drawio-desktop-headless` Docker image

## Usage

### Basic Example

```yaml
name: Export Draw.io Diagram

on: [push]

jobs:
  export:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Export diagram to SVG
        id: export
        uses: HermanPlay/drawio-exporter@v1
        with:
          input-filename: "diagram.drawio"

      - name: Print output filename
        run: echo "Generated file: ${{ steps.export.outputs.output-filename }}"
```

## Inputs

| Input            | Description                             | Required | Default |
| ---------------- | --------------------------------------- | -------- | ------- |
| `input-filename` | Full path to the input Draw.io file     | Yes      | -       |
| `format`         | Export format (pdf, png, jpg, svg, xml) | No       | `svg`   |

## Outputs

| Output            | Description                                                        |
| ----------------- | ------------------------------------------------------------------ |
| `output-filename` | Path to the generated output file. Uses basename of input filename |

## Technical Details

This action uses the [rlespinasse/drawio-desktop-headless](https://hub.docker.com/r/rlespinasse/drawio-desktop-headless) Docker image, which provides a headless version of Draw.io Desktop for automated exports.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- [rlespinasse/drawio-desktop-headless](https://github.com/rlespinasse/drawio-desktop-headless) for providing the Docker image
- [Draw.io](https://www.diagrams.net/) for the amazing diagramming tool
