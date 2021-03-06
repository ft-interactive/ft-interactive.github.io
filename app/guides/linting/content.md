# Linting

<p class="o-techdocs-leadbody">Linters are tools that help to improve the quality of your code by alerting you to possible problems.</p>

Even if code *works* in the browser, it can still have problems that will cause headaches later – it might have inconsistent indentation, or it might use 'bad' parts of the language such as the `==` operator in JavaScript.

Linters automatically alert you to sloppy code so you can clean it up.

We use the same linters that Origami uses:

- [ESLint](http://eslint.org/) for JavaScript
- [scss-lint](https://github.com/brigade/scss-lint) for Sass

<aside>
<p>NB. Older projects used JSHint instead of ESLint.</p>
</aside>


## Inline lint highlighting in your editor

We recommend setting up your editor so it shows you lint errors while you work. This can take a bit of getting used to, but it can help you to write much cleaner code.

![Lint highlighting in Atom](https://i.github-camo.com/70b6e697c9d793642414b4ea6d08dbb9678877b3/687474703a2f2f672e7265636f726469742e636f2f313352666d6972507a322e676966)

### Recommended packages

Install one of these combinations of packages to get inline lint highlighting working in your editor.

**For Atom:** [linter](https://atom.io/packages/linter) + [linter-eslint](https://atom.io/packages/linter-eslint) + [linter-scss-lint](https://atom.io/packages/linter-scss-lint)

**For Sublime Text 3:** [SublimeLinter](https://packagecontrol.io/packages/SublimeLinter) + [SublimeLinter-contrib-eslint](https://packagecontrol.io/packages/SublimeLinter-contrib-eslint) + [SublimeLinter-contrib-scss-lint](https://packagecontrol.io/packages/SublimeLinter-contrib-scss-lint)



## Blocking your build if there are lint errors

Linters should be seen as ‘helpful information’ while you're developing, and an ‘enforcement tool’ when you're building for production or committing code.

- **Don't** let lint errors prevent you doing a development build of your code. This would make it unrealistically hard to get things done. For example, having a `debugger;` statement in your code is a lint error (because you'd never want that statement to appear in production), but you might want to use this statement in development, so you can't have it blocking your development build. As long as you *know* when you have lint errors in your code (e.g. by having them highlighted in your editor, or seeing them appear in your terminal while you're working), and as long as you clean them up before committing, it's OK for them to exist.

- **Do** set up your build sequence so production builds will fail if there are lint errors. (If you really need to quickly do a production build to fix a live emergency, and lint errors are just getting in the way, then of course it's OK to temporarily disable linting.)

**Projects started with the [Starter Kit]** already follow the above advice – the development server (`npm start`) tells you about lint errors in your console while you're working, but these errors don't block things building; the build script (`npm run build`) on the other hand will refuse to continue if there are lint errors.

[starter kit]: ../starter-kit/
