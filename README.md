# Custom Tree Buildpack for Heroku

This custom buildpack installs the `tree` command-line utility on a Heroku dyno. `tree` is useful for displaying a directory tree's contents, including files, directories, and links.

## Overview

This buildpack downloads, compiles, and installs the `tree` utility during the build process, making it available in your Heroku application environment.

## Installation

To use this custom buildpack in your Heroku application, follow these steps:

1. **Add the Custom Buildpack to Your Heroku App**

   Replace `YOUR_REPOSITORY_URL` with the URL of this repository:

   ```bash
   heroku buildpacks:add --index 1 https://github.com/YOUR_USERNAME/YOUR_REPOSITORY
   ```

2. **Deploy Your Application**

   Deploy your application to Heroku:

   ```bash
   git push heroku main
   ```

## Usage

After the deployment is complete, you can verify that the `tree` utility is installed by running:

```bash
heroku run bash
```

Then, in the shell that opens, run:

```bash
tree -h
```

You should see the help message for the `tree` command, indicating that it is installed correctly.

## Buildpack Structure

- **bin/detect**: Detects that the custom buildpack is being used.
- **bin/compile**: Downloads, compiles, and installs the `tree` utility.
- **bin/release**: Placeholder script, included for completeness.

## Compiling and Installing `tree`

The `compile` script performs the following steps:

1. Downloads the `tree` source code (version 2.1.1).
2. Extracts the source code.
3. Compiles the `tree` utility.
4. Installs the compiled binary into the Heroku build directory.

## Customization

If you need to customize the buildpack or install a different version of `tree`, you can modify the `TREE_VERSION` variable in the `bin/compile` script.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgments

- The `tree` utility is developed by [Steve Baker](http://mama.indstate.edu/users/ice/tree/).
- This buildpack is inspired by the official Heroku buildpacks and the Beyond Linux® From Scratch (System V Edition) instructions for installing `tree`.

## Contributing

Contributions are welcome! If you have any improvements or suggestions, please open an issue or submit a pull request.