import { createPage } from '@vuepress/core'

export default {
  // all pages have been loaded after initialization
  async onInitialized(app) {
    // if the homepage does not exist
    if (app.pages.every((page) => page.path !== '/')) {
      // create a homepage
      const homepage = await createPage(app, {
        path: '/',
        // set frontmatter
        frontmatter: {
          layout: 'Layout',
        },
        // set markdown content
        content: `\
# Welcome to ${app.options.title}

This is Justin's default homepage
`,
      })
      // add it to `app.pages`
      app.pages.push(homepage)
    }
  },
}
