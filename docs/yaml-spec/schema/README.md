### Objective

Enable schema validation and auto-completion for custom detection YAMLs within your forked repo, streamlining detection development and ensuring alignment with your own knowledge objects and detection standards.

### Motivation

The `contentctl new` CLI wrapper enforces strict keys and values, which can make it difficult to create meaningful detections tailored to your environment (e.g., macOS, GCP). This approach provides analysts with auto-complete functionality and dropdown options, making it easier to populate required fields and adapt detection logic to environment-specific assets.


| Step | Description                                                                       | 
| ---- | --------------------------------------------------------------------------------- | 
| 1    | Create `.vscode/` folder to store project-specific editor settings                | 
| 2    | Add `schemas/detection.schema.json` for detection rule structure                  | 
| 3    | Add `.vscode/settings.json` to link schema to detection YAML files                |
| 4    | Install VSCode YAML Extension (Red Hat) for schema validation support             | 
| 5    | Create user snippet (`detection-snippets.code-snippets`) for a detection template | 
| 6    | Test typing `newdetection` into a `.yml` file and validate schema enforcement     | 

#### Example Usage


https://github.com/user-attachments/assets/77ca2d9b-91f3-42a3-b34d-44fee325b892




### Setup Instructions

#### 1. Create the `.vscode/` Folder

* Open your local cloned detections repository in VSCode.
* Create a `.vscode/` folder at the root level:

  ```bash
  mkdir .vscode
  ```
* Your folder structure should now include:

  ```
  .vscode/
  .github/
  your_detections_repo/
  README.md
  ```

#### 2. Add the Detection Schema

* Inside `.vscode/`, create a `schemas/` folder:

  ```bash
  mkdir .vscode/schemas
  ```
* Add a file named `detection.schema.json` and populate it with your environment specifics.

#### 3. Link the Schema in VSCode Settings

* Under `.vscode/`, create `settings.json` and add:

  ```json
  {
    "yaml.schemas": {
      "./.vscode/schemas/detection.schema.json": "path_to_where_your_detections_live/detections/cloud/*.yml"
    }
  }
  ```
* This applies the schema to any `.yml` files in the detections folder.

#### 4. Install the YAML Extension

* Open VSCode Extensions (`Ctrl+Shift+X`)
* Search for **YAML** by **Red Hat** and install it.
* This enables validation and autocomplete based on your schema.

#### 5. Create the Detection Template Snippet

* This will allow you to simply type `newdetection` in a new YAML file within your detections folder, and it will prepopulate this template for you. (Highly recommend to edit this as per your requirements)
* Enter `Cmd+Shift+P` in VScode
* Search for `Preferences: Configure User Snippets`
* Search for `New Global Snippets file`
* Name this file `detection-snippets.code-snippets`
* Or you can browse to the location on your local machine `/Users/<user>/Library/Application Support/Code/User/snippets`
* Add the `detection-snippets.code-snippets` to that location


#### 6. Test Your Setup

* Navigate to the detections folder and create a new YAML file.
* Type `newdetection` and use `Ctrl+Space` to trigger snippet suggestions.
* You should see schema validation and field descriptions by hovering over fields.

