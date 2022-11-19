# Perseus Tailwind Plugin

This is a simple plugin for Perseus that runs the Tailwind CLI at build time.
It will automatically download the newest version of the CLI initialize the project to look for
class names in Rust files in `src` and HTML files in `static`.
Further configuration can be done as usual in `tailwind.config.js`.

# Usage

Add the plugin to you Perseus App in your Perseus main function.

```
PerseusApp::new()
    .plugins(Plugins::new().plugin(
        perseus_tailwind::get_tailwind_plugin,
        perseus_tailwind::TailwindOptions {
            in_file: "src/tailwind.css".into(),
            out_file: "static/tailwind.css".into(),
        },
    ))
```

If you're already using plugins just add the plugin to your `Plugins` as usual.

# Using a custom binary

If you for some reason want to use a specific version of the CLI or some other CLI with the same
command line interface entirely, just place the binary with its default system-specific name
(i.e. `tailwindcss-linux-arm64`) in the project directory.

# Stability

The plugin is fairly simple and shouldn't break anything since it just executes the Tailwind CLI.
The download and installation should work on Linux, macOS and Windows on all architectures that
are supported by Tailwind, but is currently only tested on Windows x64.
