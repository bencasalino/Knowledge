---

###### NPM Installing devDependencies and Scope

While setting up your code in production:
With the --production flag (or when the NODE_ENV environment variable is set to production), npm will not install modules listed in **devDependencies**.

npm install --production

**NOTE:** The --production flag has no particular meaning when adding a dependency to a project.


While installing a npm package you can decide its scope. For example, You might not need any linting packages like EsLint to be installed in production server as it's sole purpose is for
developers.

Here are the various flags available for the same use case :

-P, --save-prod: Package will appear in your dependencies. This is the default unless -D or -O are present.

-D, --save-dev: Package will appear in your devDependencies.

-O, --save-optional: Package will appear in your optionalDependencies.

--save: Package will apperar in dependencies.

--no-save: Prevents saving to dependencies.

---
