---
title: formkit/validation
---

# @formkit/validation

:PageToc

## Introduction

The first-party validation package/plugin for FormKit. Read the [validation documentation](https://formkit.com/essentials/validation) for usage instructions.

## Functions

### createMessageName()

Given a node, this returns the name that should be used in validation messages. This is either the `validationLabel` prop, the `label` prop, or the name of the input (in that order).

#### Signature

```typescript
createMessageName(node: FormKitNode): string;
```

#### Parameters

- `node` — The node to display

#### Returns

### createValidationPlugin()

The actual validation plugin function. Everything must be bootstrapped here.

#### Signature

```typescript
createValidationPlugin(baseRules?: FormKitValidationRules): (node: FormKitNode) => void;
```

#### Parameters

- `baseRules` — Base validation rules to include in the plugin. By default, FormKit makes all rules in the formkit/rules package available via the defaultConfig.

### getValidationMessages()

Extracts all validation messages from the given node and all its descendants. This is not reactive and must be re-called each time the messages change.

#### Signature

```typescript
getValidationMessages(node: FormKitNode): Map<FormKitNode, FormKitMessage[]>;
```

#### Parameters

- `node` — The FormKit node to extract validation rules from — as well as its descendants.

## TypeScript

### FormKitValidationMessages

The interface for the localized validation message registry.

```typescript
interface FormKitValidationMessages {
  [index: string]: string | ((...args: FormKitValidationI18NArgs) => string)
}
```

### FormKitValidationRules

FormKit validation rules are structured as on object of key/function pairs where the key of the object is the validation rule name.

```typescript
interface FormKitValidationRules {
  [index: string]: FormKitValidationRule
}
```

### FormKitValidation

Defines what fully parsed validation rules look like.

```typescript
type FormKitValidation = {
  rule: FormKitValidationRule
  args: any[]
  timer: number
  state: boolean | null
  queued: boolean
  deps: FormKitDependencies
  messageObserver?: FormKitObservedNode
} & FormKitValidationHints
```

### FormKitValidationIntent

Defines what validation rules look like when they are parsed, but have not necessarily had validation rules substituted in yet.

```typescript
type FormKitValidationIntent = [string | FormKitValidationRule, ...any[]]
```

### FormKitValidationRule

Signature for a generic validation rule. It accepts an input — often a string — but should be able to accept any input type, and returns a boolean indicating whether or not it passed validation.

```typescript
type FormKitValidationRule = {
  (node: FormKitNode, ...args: any[]): boolean | Promise<boolean>
  ruleName?: string
} & Partial<FormKitValidationHints>
```
