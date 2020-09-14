# NPM / Yarn

## How to test a package locally

**Context:** You are working on project **Alpha**, and would like to test out the **Alpha** package locally inside your other project, **Beta**, without having to publish **Alpha** or perform a release. The directory structure for this scenario is as such:

```markdown
working-directory/
└ alpha/
└ beta/
```

### Initial local install:

Perform the following steps for the first time you want to test the **Alpha** package locally. For every subsequent update or change, follow the steps under the **Subsequent changes to **Alpha** project** section.

1. Inside **Alpha** | Run `yarn pack`
   - This will compress the **Alpha** project into a `.tgz` file and save it to the root directory.
   - In this scenario, this resulted in a file named `package-v1.0.0.tgz`.
2. Inside **Beta** | Run `yarn add file:../alpha/package-v1.0.0.tgz`
   - This will add the local **Alpha** package to your **Beta** project.
   - Be sure to replace `package-v1.0.0.tgz` with your file.

### Subsequent changes to **Alpha** project:

The **Alpha** package was successfully added to your **Beta** project, however the **Alpha** package is "locked" to that version. If you make changes to **Alpha** and want them to reflect in the package being used inside **Beta**, you need to do the following:

1. Inside **Alpha** | Run `yarn pack`
   - This will compress the **Alpha** project into a `.tgz` file and overwrite the current `.tgz` file in the root.
2. Inside **Alpha** | Rename the `.tgz` file to something new
   - For example, if the file was `package-v1.0.0.tgz`, you can rename it to `package-v1.0.0-local-1.tgz` (you can then continue the naming convention for future changes, such as `-local-2.tgz`, `-local-3.tgz`, etc.).
3. Inside **Beta** | Remove the `package.json` dependency source of **Alpha**
   - For example, remove the line `"alpha": "file:../alpha/package-v1.0.0.tgz"`.
4. Inside **Beta** | Run `yarn add file:../alpha/package-v1.0.0-local-1.tgz`
   - Be sure to replace the path and filename with your own.
   - This will re-add the **Alpha** package using the updated `.tgz` file contents.

**Note:** Although it is a manual process (for now), you must rename the `.tgz` file every time you want to update the package source inside Beta. This is because yarn caches the filename and not the contents.
