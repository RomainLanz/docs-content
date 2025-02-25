---
title: formkit/inputs
---

# @formkit/inputs

:PageToc

## Introduction

The official FormKit Inputs plugin. This package contains the source code for all native HTML input types. Read the [inputs documentation](https://formkit.com/essentials/inputs) for usage instructions.

## Helpers

### $attrs()

Applies attributes to a given schema section by applying a higher order function that merges a given set of attributes into the node.

#### Signature

```typescript
$attrs(attrs: FormKitSchemaAttributes | (() => FormKitSchemaAttributes), section: FormKitSchemaExtendableSection): FormKitSchemaExtendableSection;
```

#### Parameters

- `attrs` — Attributes to apply to a [FormKitSchemaExtendableSection](#formkitschemaextendablesection).
- `section` — A section to apply attributes to.

#### Returns

[FormKitSchemaExtendableSection](#formkitschemaextendablesection)

### $extend()

Extends a schema node with a given set of extensions.

#### Signature

```typescript
$extend(section: FormKitSchemaExtendableSection, extendWith: Partial<FormKitSchemaNode>): FormKitSchemaExtendableSection;
```

#### Parameters

- `section` — A section to apply an extension to.
- `extendWith` — A partial schema snippet to apply to the section.

#### Returns

[FormKitSchemaExtendableSection](#formkitschemaextendablesection)

### $for()

Applies a condition to a given schema section.

#### Signature

```typescript
$for(varName: string, inName: string, section: FormKitSchemaExtendableSection): (extensions: Record<string, Partial<FormKitSchemaNode>>) => FormKitSchemaNode;
```

#### Parameters

- `varName` — The name of the variable that holds the current instance.
- `inName` — The variable we are iterating over.
- `section` — A section to repeat.

#### Returns

[FormKitSchemaExtendableSection](#formkitschemaextendablesection)

### $if()

Applies a condition to a given schema section.

#### Signature

```typescript
$if(condition: string, then: FormKitSchemaExtendableSection, otherwise?: FormKitSchemaExtendableSection): FormKitSchemaExtendableSection;
```

#### Parameters

- `condition` — A schema condition to apply to a section.
- `then` — The section that applies if the condition is true.
- `otherwise` — (else) The section that applies if the condition is false.

#### Returns

[FormKitSchemaExtendableSection](#formkitschemaextendablesection)

### $root()

Creates a root schema section.

#### Signature

```typescript
$root(section: FormKitSchemaExtendableSection): FormKitExtendableSchemaRoot;
```

#### Parameters

- `section` — A section to make a root from.

#### Returns

[FormKitSchemaExtendableSection](#formkitschemaextendablesection)

## Features

### checkboxes()

A feature that adds checkbox selection support.

#### Signature

```typescript
checkboxes(node: FormKitNode): void;
```

#### Parameters

- `node` — A [FormKitNode](/api-reference/formkit-core#formkitnode).

### defaultIcon()

Adds icon props definition.

#### Signature

```typescript
defaultIcon(sectionKey: string, defaultIcon: string): (node: FormKitNode) => void;
```

#### Parameters

- `sectionKey` — the location the icon should be loaded.
- `defaultIcon` — the icon that should be loaded if a match is found in the user's CSS.

#### Returns

A [FormKitPlugin](/api-reference/formkit-core#formkitplugin).

### files()

A feature to add file handling support to an input.

#### Signature

```typescript
files(node: FormKitNode): void;
```

#### Parameters

- `node` — A [FormKitNode](/api-reference/formkit-core#formkitnode).

### initialValue()

A feature that ensures the input has an `initialValue` prop.

#### Signature

```typescript
initialValue(node: FormKitNode): void;
```

#### Parameters

- `node` — A [FormKitNode](/api-reference/formkit-core#formkitnode).

### localize()

Creates a new feature that generates a localization message of type ui for use on a given component.

#### Signature

```typescript
localize(key: string, value?: string): (node: FormKitNode) => void;
```

#### Parameters

- `key` — The key of the message.
- `value` — The value of the message.

#### Returns

A [FormKitPlugin](/api-reference/formkit-core#formkitplugin).

### normalizeBoxes()

A feature that normalizes box types (checkboxes, radios).

#### Signature

```typescript
normalizeBoxes(node: FormKitNode): FormKitMiddleware<{
    prop: string | symbol;
    value: any;
}>;
```

#### Parameters

- `node` — A [FormKitNode](/api-reference/formkit-core#formkitnode).

#### Returns

A [FormKitMiddleware](/api-reference/formkit-node#formkitmiddleware).

### options()

A feature that converts the options prop to usable values, to be used by a feature or a plugin.

#### Signature

```typescript
options(node: FormKitNode): void;
```

#### Parameters

- `node` — A [FormKitNode](/api-reference/formkit-core#formkitnode).

### radios()

A feature to check if the value being checked is the current value.

#### Signature

```typescript
radios(node: FormKitNode): void;
```

#### Parameters

- `node` — A [FormKitNode](/api-reference/formkit-core#formkitnode).

## Functions

### composable()

#### Signature

```typescript
composable(key: string, schema: FormKitInputSchema): FormKitSchemaComposable;
```

#### Parameters

- `key` — A new section key name.
- `schema` — The default schema in this composable slot.

#### Returns

[FormKitSchemaComposable](/api-reference/formkit-core#formkitschemacomposable)

### createLibraryPlugin()

Creates a plugin based on a list of [FormKitLibrary](/api-reference/formkit-core#formkitlibrary).

#### Signature

```typescript
createLibraryPlugin(...libraries: FormKitLibrary[]): FormKitPlugin;
```

#### Parameters

- `libraries` — One or many [FormKitLibrary](/api-reference/formkit-core#formkitlibrary).

#### Returns

[FormKitPlugin](/api-reference/formkit-core#formkitplugin)

### createSection()

Creates a new reusable section.

#### Signature

```typescript
createSection(section: string, el: string | null | (() => FormKitSchemaNode), root: true): FormKitSection<FormKitExtendableSchemaRoot>;
createSection(section: string, el: string | null | (() => FormKitSchemaNode)): FormKitSection<FormKitSchemaExtendableSection>;
createSection(section: string, el: string | (() => FormKitSchemaNode), root: false): FormKitSection<FormKitSchemaExtendableSection>;
```

#### Parameters

- `section` — A single section of schema
- `el` — The element or a function that returns a schema node.
- `root` — When true, returns a FormKitExtendableSchemaRoot. When false, returns a FormKitSchemaExtendableSection.

#### Returns

Returns a [FormKitExtendableSchemaRoot](/api-reference/formkit-core#formkitextendableschemaroot) or a [FormKitSchemaExtendableSection](/api-reference/formkit-core#formkitschemaextendablesection).

### disables()

A feature that allows disabling children of this node.

#### Signature

```typescript
disables(node: FormKitNode): void;
```

#### Parameters

- `node` — A [FormKitNode](/api-reference/formkit-core#formkitnode).

### extendSchema()

Extends a single schema node with an extension. The extension can be any partial node including strings.

#### Signature

```typescript
extendSchema(schema: FormKitSchemaNode, extension?: Partial<FormKitSchemaNode>): FormKitSchemaNode;
```

#### Parameters

- `schema` — The base schema node.
- `extension` — The values to extend on the base schema node.

#### Returns

[FormKitSchemaNode](/api-reference/formkit-core#formkitschemanode)

### findSection()

Finds a seciton by name in a schema.

#### Signature

```typescript
findSection(schema: FormKitSchemaNode[], target: string): [false, false] | [FormKitSchemaNode[], FormKitSchemaCondition];
```

#### Parameters

- `schema` — A [FormKitSchemaNode](/api-reference/formkit-core#formkitschemanode) array.
- `target` — The name of the section to find.

#### Returns

a tuple of the schema and the section or a tuple of `false` and `false` if not found.

### form()

A feature to add a submit handler and actions section.

#### Signature

```typescript
form(node: FormKitNode): void;
```

#### Parameters

- `node` — A [FormKitNode](/api-reference/formkit-core#formkitnode).

### ignore()

A feature that applies `ignore="true"` by default.

#### Signature

```typescript
ignore(node: FormKitNode): void;
```

#### Parameters

- `node` — A [FormKitNode](/api-reference/formkit-core#formkitnode).

### isSchemaObject()

Type guard for schema objects.

#### Signature

```typescript
isSchemaObject(schema: Partial<FormKitSchemaNode>): schema is FormKitSchemaDOMNode | FormKitSchemaComponent | FormKitSchemaFormKit;
```

#### Parameters

- `schema` — returns `true` if the node is a schema node but not a string or conditional.

#### Returns

`boolean`

### isSlotCondition()

Checks if the current schema node is a slot condition.

#### Signature

```typescript
isSlotCondition(node: FormKitSchemaNode): node is {
    if: string;
    then: string;
    else: FormKitSchemaNode | FormKitSchemaNode[];
};
```

#### Parameters

- `node` — A [FormKitSchemaNode](/api-reference/formkit-core#formkitschemanode).

#### Returns

`boolean`

#### Examples

```js
{
 if: '$slot.name',
 then: '$slot.name',
 else: []
} // this schema node would return true.
```

### normalizeOptions()

A function to normalize an array of objects, array of strings, or object of key-values to use an array of objects with value and label properties.

#### Signature

```typescript
normalizeOptions(options: FormKitOptionsProp): FormKitOptionsList;
```

#### Parameters

- `options` — An un
  -normalized [FormKitOptionsProp](#formkitoptionsprop).

#### Returns

A list of [FormKitOptionsList](#formkitoptionslist).

### select()

Converts the options prop to usable values.

#### Signature

```typescript
select(node: FormKitNode): void;
```

#### Parameters

- `node` — A formkit node.

### useSchema()

Creates an input schema with all of the wrapping base schema.

#### Signature

```typescript
useSchema(inputSection: FormKitSection): FormKitExtendableSchemaRoot;
```

#### Parameters

- `inputSection` — Content to store in the input section key location.

#### Returns

[FormKitExtendableSchemaRoot](/api-reference/formkit-core#formkitextendableschemaroot)

## TypeScript

### FormKitFile

A single file object in FormKit’s synthetic "FileList".

```typescript
interface FormKitFile {
  file?: File
  name: string
}
```

### FormKitOptionsItem

Options should always be formatted as an array of objects with label and value properties.

```typescript
interface FormKitOptionsItem {
  __original?: any
  [index: string]: any
  attrs?: {
    disabled?: boolean
  } & Record<string, any>
  label: string
  value: unknown
}
```

### FormKitOptionsPropExtensions

Allows for prop extensions to be defined by using an interface whose keys are ignored, but values are applied to a union type. This allows for any third party code to extend the options prop by using module augmentation to add new values to the union type.

```typescript
interface FormKitOptionsPropExtensions {
  arrayOfNumbers: number[]
  arrayOfStrings: string[]
  optionsList: FormKitOptionsList
  valueLabelPojo: Record<string | number, string>
}
```

### FormKitSchemaExtendableSection

A function that is called with an extensions argument and returns a valid schema node.

```typescript
interface FormKitSchemaExtendableSection {
  _s?: string
  (extensions: Record<string, Partial<FormKitSchemaNode>>): FormKitSchemaNode
}
```

### FormKitSection

A function that when called, returns a function that can in turn be called with an extension parameter.

```typescript
interface FormKitSection<T = FormKitSchemaExtendableSection> {
  (...children: Array<FormKitSchemaExtendableSection | string>): T
}
```

### FormKitSyntheticPropsExtensions

Synthetic props are props that are not explicitly declared as props, but should be treated as props to the outside world.

```typescript
interface FormKitSyntheticPropsExtensions {
  accept: string
  action: string
  actions: boolean
  disabled: string | boolean
  enctype: string
  help: string
  ignore: string | boolean
  label: string
  max: string | number
  method: string
  min: string | number
  multiple: string | boolean
  options: FormKitOptionsProp
  preserve: string | boolean
  preserveErrors: string | boolean
  step: string | number
}
```

### FormKitFileValue

A synthetic array-based "FileList".

```typescript
type FormKitFileValue = FormKitFile[]
```

### FormKitInputSchema

Either a schema node, or a function that returns a schema node.

```typescript
type FormKitInputSchema =
  | ((
      children?: string | FormKitSchemaNode[] | FormKitSchemaCondition
    ) => FormKitSchemaNode)
  | FormKitSchemaNode
```

### FormKitOptionsList

An array of option items.

```typescript
type FormKitOptionsList = FormKitOptionsItem[]
```

### FormKitOptionsProp

The types of options that can be passed to the options prop.

```typescript
type FormKitOptionsProp =
  FormKitOptionsPropExtensions[keyof FormKitOptionsPropExtensions]
```

### FormKitSyntheticProps

The synthetic prop types.

```typescript
type FormKitSyntheticProps = {
  [Property in keyof FormKitSyntheticPropsExtensions]: FormKitSyntheticPropsExtensions[Property]
}
```
