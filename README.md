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
