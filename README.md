# LaterJS Typings Issue

Current LaterJS typings are not compatible with `strictNullChecks` on newer versions of TSC.

## Steps to Replicate

0. `git clone` this repo
1. `npm install`
2. Compile with `node_modules/typescript/bin/tsc`

This will result in numerous null check errors such as the following:

```
node_modules/@types/later/index.d.ts(138,9): error TS2411: Property 'Y_b' of type 'number[] | undefined' is not assignable to string index type 'number[]'.
```
## Remedy

Several actions will make the compilation errors go away:

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
2. Change line 145 to `[timeperiodAndModifierName: string]: number[] | undefined;`.
3. Use the `extends` keyword for custom changes.
