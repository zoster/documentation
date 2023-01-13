---
title: Decoupled Kit
subtitle: Front End Starters
description:
contenttype: [guide]
innav: [true]
categories: [api]
newcms: [--]
audience: [--]
product: [decoupled]
integration: [--]
tags: [--]
layout: guide
permalink: docs/guides/api/decoupled/frontend
anchorid: frontend
showtoc: false

---

<TabList>

<Tab title="Next.js" id="next" active={true}>

<Accordion title="Differences Between SSG, ISR, and SSR" id="static-dynamic" icon="info-sign">

## Before You Begin

This document is meant to supplement
[Next.js documentation](https://nextjs.org/docs) as a quick comparison of
Next.js's Static Site Generation (SSG), Incremental Static Regeneration (ISR)
and Server Side Rendering (SSR) modes in the context of Pantheon, and some
common use cases for each. This document will not cover client side rendering
(CSR).

See the
[Next.js overview on data fetching](https://nextjs.org/docs/basic-features/data-fetching/overview)
for more information on each rendering mode.

## What Is Static Site Generation (SSG)?

A static page in Next.js is a React component exported from a file under the
`pages` directory that has data fetching inside of `getStaticProps`—which is
also exported from the same file—or no data fetching at all. Static pages are
generated at build time. Static pages utilizing dynamic routing and
`getStaticProps` must also export a `getStaticPaths` function, which is used to
specify the exact path for the static content. See the
[official `getStaticPaths` documentation](https://nextjs.org/docs/basic-features/data-fetching/get-static-paths)
for more information.

Static pages can be served with `next export` without a Node.js server, however,
many of the features that make Next.js worth using are not enabled this way and
we do not recommend it.

### Common Use Cases

- Pages with content that is the same for all users
- Pages that can be publicly cached
- Pages that does not require data from an outside source

## What Is Incremental Static Regeneration (ISR)?

It is possible to update static pages after they have been built with new
content by utilizing
[Incremental Static Regeneration (ISR)](https://nextjs.org/docs/basic-features/data-fetching/incremental-static-regeneration).
To enable ISR, add the `revalidate` prop to `getStaticProps`. The revalidate
prop defines the number of seconds that the server will wait before rerunning
`getStaticProps`. This is known as stale-while-revalidate

## What Is Server Side Rendering (SSR)?

A dynamic page in Next.js is a React component exported from a file under the
`pages` directory that has data fetching inside of `getServerSideProps`. Dynamic
pages are generated at request time.

### Common Use Cases

- Pages that are user specific
- Pages that require authentication
- Pages requiring data fetched at request time

## Summary Of Differences

- Next.js pages can export an async function, `getStaticProps` or
  `getServerSideProps`, which runs on the server and returns props to the
  component on the client side
- SSG'd pages fetch data at build time using `getStaticProps` or do not have any
  data fetching at all
- ISR'd pages are SSG pages that refetch data after a given `revalidate` time
  has expired
- SSR'd pages fetch data at the time the page is requested

## Implementing Next.js Data Fetching

For a walk-through of fetching data with `getStaticProps` and
`getServerSideProps`, see
[Your First Next.js & Drupal Customization](./Next.js%20%2B%20Drupal/your-first-customization.md)
or
[Your First Next.js & WordPress Customization](./Next.js%20%2B%20WordPress/your-first-customization.md),
or look through the
[`next-drupal-starter`](https://github.com/pantheon-systems/decoupled-kit-js/tree/canary/starters/next-drupal-starter/)
or
[`next-wordpress-starter`](https://github.com/pantheon-systems/decoupled-kit-js/tree/canary/starters/next-wordpress-starter)
for a starting point or inspiration


</Accordion>

<Accordion title="Setting Path Prefix For Testing Locally" id="set-base-path" icon="wrench">

## Before You Begin

This guide assumes you are testing a Next.js site locally which is to be hosted at a subpath of the root, for example `/docs`, by using the [Next.js `basePath` feature](https://nextjs.org/docs/api-reference/next.config.js/basepath).

## Setting The Path Prefix
See the Next.js guide on [Adding a Base Path](https://nextjs.org/docs/api-reference/next.config.js/basepath) for information on setting the `basePrefix` if you are not using the starter kit.

If you are using the `@pantheon-systems/next-drupal-starter` or the `@pantheon-systems/next-wordpress-starter`, the environment variable `process.env.PANTHEON_UPLOAD_PATH` will be automatically set as the `basePath` in the `next.config.js`. To test this locally, set the `PANTHEON_UPLOAD_PATH` in your `.env.development.local` to the path you would like to test.


## Verify Links And Assets
If you are adding the `basePath` to an app that did not previously use it, you may need to refactor some in app links and paths to static assets. [Links using the `next/link` component will automatically use the `basePath`](https://nextjs.org/docs/api-reference/next.config.js/basepath#links). You will need to update the `src` if using the `next/image` component for static assets. See the [Next.js docs on images and `basePath`](https://nextjs.org/docs/api-reference/next.config.js/basepath#images) for more information.

</Accordion>


* [Next.js + Drupal](/guides/api/decoupled/frontend-starters/nextjs/nextjs-drupal/introduction)

* [Next.js + WordPress](/guides/api/decoupled/frontend-starters/nextjs/nextjs-wordpress/introduction)

</Tab>


<Tab title="Gatsby" id="gatsby">
</Tab>

</TabList>