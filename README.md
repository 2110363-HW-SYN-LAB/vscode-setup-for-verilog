# vscode-setup-for-verilog
### Creating a New VSCode Profile

It is strongly recommended to create a new VSCode profile for Verilog development to keep your settings and extensions organized.

### How to Create a New Profile

1. Open VSCode.
2. Open the Command Palette (`Ctrl+Shift+P` or `Cmd+Shift+P` on macOS).
3. Type `Profiles: Create Profile` and select it.
4. Enter a name for your new profile, e.g., `Verilog Development`.
5. Click `Create`.

Alternatively, you can use the GUI:

1. Click on the `Manage` icon in the bottom left corner.
2. Hover over `Profiles`.
3. Select `Profiles` > `Create Profile`.
4. Enter a name for your new profile, e.g., `Verilog Development`.
5. Click `Create`.
6. Set other options as needed.

### How to Apply VSCode Settings

1. Open the Command Palette (`Ctrl+Shift+P` or `Cmd+Shift+P` on macOS).
2. Type `Preferences: Open Settings (UI)` and select it.
3. Make sure you are in the correct profile by checking the profile name in the bottom left corner.
4. Adjust your settings as needed for Verilog development.

### Recommended VSCode Extensions

- [Verilog-HDL/SystemVerilog/Bluespec](https://marketplace.visualstudio.com/items?itemName=mshr-h.VerilogHDL): For snippet, syntax hightlight and formatter
- [Verible](https://marketplace.visualstudio.com/items?itemName=chipsalliance.verible): For linter

### Installing Dependencies

To use the recommended extensions and settings, you need to install `verible`. Follow these steps to install it:

1. **Using Homebrew (macOS):**
    ```sh
    brew tap chipsalliance/verible
    brew install verible
    ```
    Ref: https://github.com/chipsalliance/homebrew-verible

2. **Using Pre-built Binaries:**
    Download the latest release from the [Verible GitHub Releases](https://github.com/chipsalliance/verible/releases) page and follow the installation instructions for your platform.

3. **Building from Source:**
    Follow the instructions on the [Verible GitHub repository](https://github.com/chipsalliance/verible) to build and install from source.

Make sure `verible-verilog-ls` is in your system's PATH so that VSCode can use it.

### VSCode Settings for Verilog

To ensure a smooth Verilog development experience, add the following settings to your VSCode configuration:

```json
{
    "[verilog]": {
        "editor.defaultFormatter": "mshr-h.veriloghdl"
    },
    "verilog.formatting.verilogHDL.formatter": "verible-verilog-format",
    "verilog.formatting.veribleVerilogFormatter.arguments": "--indentation_spaces=4 --case_items_alignment=align --assignment_statement_alignment=align --class_member_variable_alignment=align --distribution_items_alignment=align --enum_assignment_statement_alignment=align --formal_parameters_alignment=align --module_net_variable_alignment=align --named_parameter_alignment=align --named_port_alignment=align --port_declarations_alignment=align --struct_union_members_alignment=align",
    "verible.arguments": [
        "--rules=-always-comb,-unpacked-dimensions-range-ordering,-explicit-parameter-storage-type",
        "--file_list_path=${workspaceFolder}/verible.filelist",
        "--indentation_spaces=4"
    ],
    "verible.path": "verible-verilog-ls",
}
```

- `"[verilog]": { "editor.defaultFormatter": "mshr-h.veriloghdl" }`: Sets the default formatter for Verilog files to the Verilog-HDL extension.
- `"verilog.formatting.verilogHDL.formatter": "verible-verilog-format"`: Specifies Verible as the formatter for Verilog files.
- `"verilog.formatting.veribleVerilogFormatter.arguments"`: Provides arguments for the Verible formatter to align various elements and set indentation spaces.
- `"verible.arguments"`: Lists additional arguments for Verible, including rules to disable, the file list path, and indentation spaces.
- `"verible.path"`: Specifies the path to the Verible language server.

These settings help maintain consistent code formatting and improve the development experience when working with Verilog in VSCode.