Its quite obtuse, but the QuickAdd plugin has the concept of **choices**. A **choice** is what actually shows up in the command palette; while the macro/multi/template/capture is what gets run by that choice.

# Macros
You need to manually create `.js` scripts (ideally in a folder called `Scripts` or something). QuickAdd looks for `.js` userscripts recursively in the vault. You can then add them as command palette choices by creating a **Choice** that points to that user script.

## Variables
QuickAdd passes an object `params` to your script's exported function. You can grab the QuickAdd API from here, as well as the Obsidian app object. There is also a `variables` member that can be used to:
- Pass variables from one userscript to another (e.g. to chain macros)
- Put values into templates using the `{{VALUE: <var name>}}` syntax. This is useful for instantiating templates from a macro!