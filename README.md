# More flexible Doxygen GitHub Pages Deploy Action

GitHub Action for making and deploying Doxygen documentation to a GitHub pages branch

## Basic Usage

To deploy docs on every push to the `main` branch, create a new file in the `.github/workflows/` directory called `doxygen-gh-pages.yml` with the following contents:

```yml
name: Doxygen GitHub Pages Deploy Action

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: hwyao/doxygen-github-pages-action@v0.1.0
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
```

The Doxyfile is at the root of the repository, and the HTML files will be generated in the `docs/html` folder. The action will automatically push the generated documentation to the `main` branch of the repository.

## Options

- `github_token` (required): GitHub token for pushing to repo. See the [docs](https://git.io/passing-token) for more info.
- `running_folder` (optional): Folder where the action is running. Defaults to the root of the repository.
- `html_folder` (optional): Folder where the HTML files are generated. Defaults to `docs/html`.
- `config_file` (optional): Name of the Doxygen configuration file. Defaults to `Doxyfile`.
- `target_repo` (optional): The repository to deploy to. Defaults to the current repository.
- `target_folder` (optional): Directory within the deployment branch to push to. Defaults to empty (root).
- `target_branch` (optional): The branch to deploy to. Defaults to `main`.

## Advanced Usage

Here is an example of a `.github/workflows/doxygen-gh-pages.yml` file with more advanced configuration:

```yml
name: Doxygen GitHub Pages Deploy Action

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: hwyao/doxygen-github-pages-action@v0.1.0
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          running_folder: docs
          html_folder: docs/html
          config_file: Doxyfile
          target_branch: main
```

## Credits

This project is based on the work of [DenverCoder1](https://github.com/DenverCoder1/doxygen-github-pages-action).

## License

This work is under an [MIT license](LICENSE)

## Support

If you like this project, give it a ⭐ and share it with friends!
