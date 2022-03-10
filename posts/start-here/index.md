---
title: Start Here
date: 2022-03-10
---

<script>
    import ThemeToggle from '$lib/components/ThemeToggle.svelte'
</script>

This starter is based off [this awesome template](https://github.com/mattjennings/sveltekit-blog-template) by [Matt Jennings](https://twitter.com/mattjennings44). If you haven't already, read [Matt's post](https://sveltekit-blog-template.vercel.app/posts/getting-started) on how the starter works and come back after to read about what I've added.

## Minor Additions

I've added a couple more exports to `src/lib/info.js` file for social media links. Update them with your own info and links, or delete the SocialLinks component all together, up to you!

I also added the search bar on the posts page, it currently searches the posts by title.

## Additional Components

Here's a quick summary of everything I've added on top of Matt's original template:

### Header

The header contains the default navigation as well as the MobileNav and ThemeToggle components.

### Footer

The footer is extremely minimal and was mostly included for organizational purposes. Replace the content by manually editing the content (it's just a paragraph).

### MobileNav

I extracted the mobile navigation out into it's own component to keep things organized and maintainable. I added some fun Svelte transitions.

### ThemeToggle

This component switches the theme from dark mode to light mode. It is used in both the Header component as well as the MobileNav component. You can even include it in your markdown posts!

<ThemeToggle />

### SocialLinks

Pretty self explanatory. I could've hard coded but I thought it was slightly easier to edit this way. This component is only used on the about page, but could be modified and used in other places, such as the footer.

### Typing

This is the Hero section component. To customize the phrases that are being "typed" head to the Typing.svelte file and change the phrases in the array.

---

I hope you find this starter useful! Thanks to Matt for creating and sharing your original template!
