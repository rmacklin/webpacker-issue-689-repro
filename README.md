Reproduction repository for https://github.com/rails/webpacker/issues/689

Steps to reproduce:

1. `git clone git@github.com:rmacklin/webpacker-issue-689-repro.git`
2. `cd webpacker-issue-689-repro/test_app`
3. `yarn install`
4. `bin/webpack`

This will error out with the following message:

```
Invalid configuration object. Webpack has been initialised using a configuration object that does not match the API schema.
 - configuration.entry should be one of these:
   object { <key>: non-empty string | [non-empty string] } | non-empty string | [non-empty string] | function
   The entry point(s) of the compilation.
   Details:
    * configuration.entry should NOT have less than 1 properties ({
        "keyword": "minProperties",
        "dataPath": ".entry",
        "schemaPath": "#/oneOf/0/minProperties",
        "params": {
          "limit": 1
        },
        "message": "should NOT have less than 1 properties",
        "schema": 1,
        "parentSchema": {
          "minProperties": 1,
          "additionalProperties": {
            "oneOf": [
              {
                "description": "The string is resolved to a module which is loaded upon startup.",
                "minLength": 1,
                "type": "string"
              },
              {
```

However, if you `git checkout fix-glob-suffix` and rerun `bin/webpack`, it will
successfully compile the entry point.
