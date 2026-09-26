# How do I create a plugin for yt-dlp?
A template plugin package repository is available at [yt-dlp/yt-dlp-sample-plugins](https://github.com/yt-dlp/yt-dlp-sample-plugins).

- To see how to write extractors in general, see the [yt-dlp developer instructions](https://github.com/yt-dlp/yt-dlp/blob/master/CONTRIBUTING.md#developer-instructions).
- For information regarding the plugin spec, see the [plugins section of the yt-dlp README](https://github.com/yt-dlp/yt-dlp#plugins).

## Getting Started

1. [Create a new repository based on yt-dlp/yt-dlp-sample-plugins](https://github.com/yt-dlp/yt-dlp-sample-plugins/generate)
2. Check out the source code with:
    `git clone git@github.com:YOUR_GITHUB_USERNAME/YOUR_REPOSITORY.git`
3. [Configure your IDE's run and debug configuration](#Run-and-debug-configuration) (optional)
4. Write your plugin code in the `yt_dlp_plugins/<type>` folder (where type is either `extractor` or `postprocessor`). See the sample plugins provided and the [yt-dlp developer instructions](https://github.com/yt-dlp/yt-dlp/blob/master/CONTRIBUTING.md#developer-instructions) for more details. 
    - Some instructions given will not apply to plugin development, but should give you a good idea on what to do. 
    - The method for testing extractor plugins is the same as with built-in ones.
5. [Configure your plugin package](#Configuring-your-plugin-package)
6. [Add](https://git-scm.com/docs/git-add) the new files, [commit](https://git-scm.com/docs/git-commit) them and [push](https://git-scm.com/docs/git-push) the result, like this:
    ```git
     $ git add yt_dlp_plugins setup.cfg README.md
     $ git commit -m 'Add yourplugin plugin'
     $ git push origin master
    ```

---

## Configuring your plugin package
1. Modify [setup.cfg](https://github.com/yt-dlp/yt-dlp-sample-plugins/blob/master/setup.cfg) with your plugin's name and version. It is recommended to bump the version whenever you make changes or a new release.
2. Update the installation instructions on [README.md](https://github.com/yt-dlp/yt-dlp-sample-plugins/blob/master/README.md) to point to this repository.
3. Add `yt-dlp-plugins` to the repository tags for discoverability.
4. Be sure to remove any of the sample extractors/post-processors.

You should NOT set `yt-dlp` as a dependency, because then users who installed yt-dlp with a method other than pip will end up with two `yt-dlp`s after installing your plugin.

## Run and debug configuration
1. Set your IDE's run configuration to point to the `yt_dlp` Python module.
2. Add your project's root directory containing `yt_dlp_plugins` to `PYTHONPATH` environment variable (this may not be necessary with some IDE run configurations).
3. The `yt_dlp_plugins` folder should be automatically picked up by yt-dlp (run with `-v` to check).

## Importing extractors from other plugins

```py
from yt_dlp_plugins.extractor.example import ExampleIE
```

This works regardless of where the `example` plugin is installed on the system, as long as yt-dlp can find it. 
Your IDE may not be able to resolve the import, but it will work at runtime.

If the user does not have the `example` plugin installed, the import will fail and your extractor will not be imported (but yt-dlp will continue to run). 

The same applies for any other plugin type.

## Poetry configuration

If you want your plugin to be installable with [poetry](https://python-poetry.org/), you can add the following to your `pyproject.toml`:

```
[tool.poetry]
...
packages = [{ include = "yt_dlp_plugins" }]
...
```

See the [Poetry documentation](https://python-poetry.org/docs/pyproject/#packages) for more details.

## Distributing your plugin as a single file

You can put a pip command in your README, but that doesn't serve `yt-dlp.exe` users very well.
In this case, it's more user friendly to package your plugin up into a single file. That way you can tell people to "drop this one file in the right place and it'll sort itself", the same way dependencies like ffmpeg and deno are handled. You can still let pip users install with pip, of course.

> `.zip`, `.egg` and `.whl` archives containing a `yt_dlp_plugins` namespace folder in their root are also supported as plugin packages.

The easiest option is to distribute the `.whl` you get when you build the plugin package. Then you can say "download the .whl and put it in [such-and-such directory](https://github.com/yt-dlp/yt-dlp#installing-plugins)".

HOWEVER, this may come back to haunt you if you ever decide to add a third-party dependency. (`.whl`s are handled no differently from plain `.zip` files, yt-dlp will not install any dependencies.)

A solution to this is to build a `.zip` file with third-party dependencies bundled in. This needs some custom import handling to get yt-dlp to import the dependencies from the `.zip`.

You can see a model implementation of a plugin bundle in Grub4K's `yt-dont-lock-p` plugin:
- [Dependency handling](https://github.com/Grub4K/yt-dont-lock-p/blob/ff3b6e1d42ce8584153ae27544d2c05b50ab5954/yt_dlp_plugins/postprocessor/yt_dont_lock_p/__init__.py#L23-L46)
- [Build script](https://github.com/Grub4K/yt-dont-lock-p/blob/0b71dad39566fca756c51f22c51a780de26401d8/.github/workflows/release.yml#L19-L35)

Then you can hook up your big fat download button to point to that `.zip`, tell pip users the pip command, and everything is happy and lovely.
