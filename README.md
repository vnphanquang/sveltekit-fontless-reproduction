# Reproduction: Fontless Integration in SvelteKit App

This is a reproduction to show that [fontless](https://github.com/unjs/fontaine/tree/main/packages/fontless) 
currently does not work in SvelteKit app.

## Steps to Reproduce

1. clone the repository,
2. install dependencies (`pnpm install`),
3. run the development server (`pnpm dev`),
4. navigate to browser dev site (likely `http://localhost:5173/`, but see stdout from (3) for exact port),

Expected: texts should be rendered with `Lora` font.

Actual: Lora font fails to load, 404 error is shown from stderr of dev server:

```
Not found: /_fonts/c_DSuNEM0CpwGm0nBvjzlSOr1XfKIEkPNUFNOhh_1P0-NRhFW74EONtAcgszUyhCXAKYSyy3UIWLEug_n4MLLDw.woff
```

## Further Discussion

The `_fonts` directory does get created in build output (`pnpm build`), but it goes into the wrong place.

```
.svelte-kit/output/
    _fonts/ <-- where it is created
    client/
        _fonts/ <-- where it should have been
    server/
```

So perhaps I suspect this has something to do with Vite environments. As the time of this writing, I believe
SvelteKit builds 2 bundles, one for client (`client` environment) and one for server (`ssr` environment).

## Code of Interest

Font is loaded at [src/routes/+page.svelte](./src/routes/+page.svelte):

```css
main {
    font-family: Lora, serif;
}
```

