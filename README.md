# LaterJS Typings Issue

Current LaterJS typings are not compatible with `strictNullChecks` on newer versions of TSC.

## Steps to Replicate

0. `git clone` this repo
1. `npm install`
2. Compile with `node_modules/typescript/bin/tsc`

## Remedy

There are two solutions:

0. Change `strictNullChecks` to `false`. Compilation completes.
1. Comment out the following lines within `interface Recurrence`:
```
        /*
         * Custom Time Periods and Modifiers
         * For acces to custom time periods created as extension to the later static type
         * and modifiers created on the later modifier static type.
         */
        [ timeperiodAndModifierName: string ]: number[];
```

The `Custom Time Periods and Modifiers` functionality might be attainable via interface extension.