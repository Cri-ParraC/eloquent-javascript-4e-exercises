# Circular dependencies

A circular dependency is a situation where module A depends on B, and B also, directly or indirectly, depends on A. Many module systems simply forbid this because whichever order you choose for loading such modules, you cannot make sure that each module's dependencies have been loaded before it runs.

CommonJS modules allow a limited form of cyclic dependencies. As long as the modules don't access each other's interface until after they finish loading, cyclic dependencies are okay.

The `require` function given [earlier in this chapter](https://eloquentjavascript.net/10_modules.html#require) supports this type of dependency cycle. Can you see how it handles cycles?

<details>
<summary>Hint</summary>

The trick is that `require` adds the interface object for a module to its cache _before_ it starts loading the module. That way, if any `require` call made while it is running tries to load it, it is already known, and the current interface will be returned, rather than starting to load the module once more (which would eventually overflow the stack).

</details>

---

From [Eloquent JavaScript, Chapter 10: Modules](https://eloquentjavascript.net/10_modules.html).
