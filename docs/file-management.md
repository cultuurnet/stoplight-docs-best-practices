# File management

## Markdown files

**The structure of the markdown files inside your `docs` directory directly translates to the URL that they will be accessible at.** For this reason it is advised to keep your file structure as simple as possible to avoid files being moved from one directory to another at some point, which would break existing links that have been shared with integrators or have been referenced inside our own documentation.

Additionally your filenames should be structured as URL slugs, not human-readable text, to avoid hard-to-read links.

- ✅ **Use lowercased slugs with dashes** as filenames, for example `good-example.md` instead of `Bad example.md`
- ✅ **Store markdown files in the root of your docs directory**, for example `/docs/good-example.md` instead of `/docs/bad-example/do-not-do-this.md`
- ❌ **Do not rename** existing files once your project has become publicly accessible to avoid broken links

> ##### Structure and names of pages in the sidebar
> The structure of your files and folders also determines how your project's sidebar is structured by default. So by following the tips above you will end up with a very badly ordered overview in your sidebar. 
>
> However, you can override this behavior by **[customizing the sidebar](./customizing-the-sidebar.md)**. This way you can optimize your file structure for URLs first, and still have control over how the sidebar is structured visually.
>
> Manually structuring your sidebar might seem like a lot of work at first, but it is an investment that will allow a lot more flexibility down the line if you set it up from the start of your project!
>
> This is also the reason that it is advisable to not use subdirectories inside `docs`, so you can still easily move pages around between sections in your sidebar without ending up with incorrect or broken URLs.

<!-- theme: success -->

> ##### Exceptions
> The rule about having no subdirectories is strongly encouraged advice, but not a hard rule. You might have a good reason to use (some) subdirectories after all in the `docs` folder of your project. If you do, **take great care to prepare the directory structure beforehand and keep it as minimal and simple as possible**.

- ❌ If you do use subdirectories after all, **do not rename directories or move files** around after they have become publicly available

## Images

As with Markdown files, your image assets should be stored in a **single directory level**. Ideally this would be `/assets/images` (the default in Stoplight). This way you drastically reduce the chances of accidentally ending up with broken images when images would inevitably be moved around directories. It also makes direct links to images (in email, chat, ...) more durable and less likely to break.

The filenames of your images should also be structured as **URL slugs**, so `good-image-filename.png` instead of `Bad image filename.png`