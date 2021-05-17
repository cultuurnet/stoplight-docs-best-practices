# File management

**The structure of the files inside your `docs` directory directly translates to the URL that they will be accessible at.** For this reason it is advised to keep your file structure as simple as possible to avoid files being moved from one directory to another at some point, which would break existing links that have been shared with integrators or have been referenced inside our own documentation.

Additionally your filenames should be structured as URL slugs, not human-readable text, to avoid hard-to-read links.

- ✅ Use lowercased slugs with dashes as filenames, for example `good-example.md` instead of `Bad example.md`
- ✅ Keep directory structures limited to **one level** at most inside `docs`, for example `/docs/my-guide.md` or `/docs/my-directory/my-guide.md`
- ❌ Do not change the name of existing files or directories once your project has become publicly accessible to avoid broken links

> The structure of your files and folders also determines how your project's sidebar looks by default. However, you can override this by [customizing the sidebar](./customizing-the-sidebar.md).