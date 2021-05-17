# File management

**The structure of the files inside your `docs` directory directly translates to the URL that they will be accessible at.** For this reason it is advised to keep your file structure as simple as possible to avoid files being moved from one directory to another at some point, which would break existing links that have been shared with integrators or have been referenced inside our own documentation.

Additionally your filenames should be structured as URL slugs, not human-readable text, to avoid hard-to-read links.

- ✅ **Use lowercased slugs with dashes** as filenames, for example `good-example.md` instead of `Bad example.md`
- ✅ **Keep directory structures limited** to one level at most inside `docs`, for example `/docs/my-guide.md` (preferred) or `/docs/my-directory/my-guide.md` (if you foresee naming conflicts between files in different sections in your sidebar)
- ❌ **Do not rename** existing files or directories once your project has become publicly accessible to avoid broken links
- ❌ **Do not move** existing files to another directory once your project has become publicly accessible to avoid broken links

> ##### Structure of pages in the sidebar
> The structure of your files and folders also determines how your project's sidebar is structured by default. However, you can override this by **[customizing the sidebar](./customizing-the-sidebar.md)**. This way you can optimize your files and folders for URLs first, and still have control over how the sidebar is structured.
>
> This is also the reason that it is advisable to keep the amount of folder levels to none or one at most, so you can still easily move pages around between sections in your sidebar without ending up with incorrect URLs (since you should never move or rename files after they have been publicly published).