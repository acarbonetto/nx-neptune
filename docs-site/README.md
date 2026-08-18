# nx-neptune docs-site

Documentation site for [nx-neptune](https://github.com/awslabs/nx-neptune), built
with [Astro](https://astro.build/) and [Starlight](https://starlight.astro.build/).

## Local development

```bash
npm install
npm run dev      # start the dev server at http://localhost:4321/nx-neptune
npm run build    # build the static site into dist/
npm run preview  # preview the production build locally
```

Documentation pages live in `src/content/docs/`. The sidebar is configured in
`astro.config.mjs`.

## What's New

The "What's New" section is powered by the [`starlight-blog`](https://starlight-blog-docs.vercel.app/)
plugin, registered in `astro.config.mjs`. Posts live in
`src/content/docs/news/` and are published at `/news`, with an RSS feed at
`/news/rss.xml`.

### Adding a new post

1. Create a new Markdown (`.md`) or MDX (`.mdx`) file in `src/content/docs/news/`,
   e.g. `src/content/docs/news/my-post.md`. The file name becomes the URL slug
   (`/news/my-post`).
2. Add frontmatter at the top of the file:

   ```markdown
   ---
   title: My post title
   date: 2026-07-20
   excerpt: A short summary shown in the post list.
   authors: nxNeptuneTeam
   tags:
     - announcements
   ---

   Your post content goes here, written in Markdown.
   ```

   | Field     | Required | Notes                                                                 |
   | --------- | -------- | --------------------------------------------------------------------- |
   | `title`   | Yes      | Post title.                                                           |
   | `date`    | Yes      | Publication date (`YYYY-MM-DD`). Posts are sorted newest first.       |
   | `excerpt` | No       | Short summary shown in the post list and used for metadata.           |
   | `authors` | No       | Author key(s) defined in `astro.config.mjs`, or inline author object. |
   | `tags`    | No       | List of tags; each generates a `/news/tags/<tag>` page.               |

3. Authors are defined once in the `starlightBlog({ authors: { ... } })` config in
   `astro.config.mjs`. To add a new author, add an entry there and reference its
   key from a post's `authors` field.
4. Run `npm run dev` and visit `/news` to preview your post.

For the full list of supported frontmatter and configuration options, see the
[starlight-blog documentation](https://starlight-blog-docs.vercel.app/).
