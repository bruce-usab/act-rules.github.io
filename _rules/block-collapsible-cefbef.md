---
id: cefbef
name: Block of content is expandable and collapsible
rule_type: atomic
description: |
  This rule checks that repeated blocks of content are expandable and collapsible
accessibility_requirements:
  wcag-technique:SCR28: # Using an expandable and collapsible menu to bypass block of content
    forConformance: false
    failed: not satisfied
    passed: satisfied
    inapplicable: further testing needed
input_aspects:
  - DOM Tree
  - CSS styling
authors:
  - Jean-Yves Moyen
  - Anne Thyme Nørregard
---

## Applicability

This rule applies to any [document](#https://dom.spec.whatwg.org/#concept-document) where the [document element](#https://dom.spec.whatwg.org/#document-element) is an HTML `html` element.

## Expectations

For each [section of repeated content](#repeated-content) in the test target, there exists some [user interface component](https://www.w3.org/TR/WCAG21/#dfn-user-interface-components) which:
- is [visible](#visible) and [included in the accessibility tree](#included-in-the-accessibility-tree); and 
- allows to toggle both [visibility](#visible) and [inclusion in the accessibility tree](#included-in-the-accessibility-tree) of this [section of repeated content](#repeated-content).

## Assumptions

This rule assumes that [sections of repeated content](#repeated-content) have already been identified within the test target, for example by comparison with other test targets within the same website, or any other means.

## Accessibility Support

_There are no major accessibility support issues known for this rule._

## Background

- [SCR28: Using an expandable and collapsible menu to bypass block of content](https://www.w3.org/WAI/WCAG21/Techniques/client-side-script/SCR28)

## Test Cases

### Passed

#### Passed Example 1
The link to skip repeated content is visible, is included in the accessibility tree, and links to a valid HTML element.
```html
<!DOCTYPE html>
<html lang="en">
  <head><title></title></head>
  <body>
    <nav>
      <a href="#main-content">Skip to main content</a>
    </nav>
    <!-- Repeated content  -->
    <main id="main-content">Main Content</main>
  </body>
</html>
```

#### Passed Example 2
The link to skip repeated content can be toggled to visible through keyboard focus.
```html
<!DOCTYPE html>
<html lang="en">
  <head><title></title>
    <style>
      #skipNav{
        height:100px;
        position:absolute;
        top:-100px;
      }
      #skipNav:focus{
        top:0px;
      }
    </style>
  </head>
  <body>
  <nav id="skipNav">
    <a href="#main-content">Skip to main content</a>
  </nav>
  <!-- Repeated content -->
  <main id="main-content">Main Content</main>
  </body>
</html>
```

#### Passed Example 3
The link to skip repeated has an `aria-label` to provide an accessible name.
```html
<!DOCTYPE html>
<html lang="en">
  <head><title></title></head>
  <body>
  <div>
    <a href="#main-content" aria-label="Skip to main content"></a>
  </div>
  <!-- Repeated content -->
  <div id="main-content">Main Content</div>
  </body>
</html>
```
<!-- role for navigation element -->
### Failed

#### Failed Example 1
The is no link to skip repeated content.
```html
<!DOCTYPE html>
<html lang="en">
  <head><title></title></head>
  <body>
    <!-- Repeated Content -->
    <div id="main-content">Main Content</div>
  </body>
</html>
```

#### Failed Example 2
The link to skip repeated content is not the first focusable element within the `body`.
```html
<!DOCTYPE html>
<html lang="en">
  <head><title></title></head>
  <body>
    <a href="#nowhere">Link to nowhere</a>
    <nav>
      <a href="#main-content">Skip to main content</a>
    </nav>
    <!-- Repeated Content -->
    <div id="main-content">Main Content</div>
  </body>
</html>
```

#### Failed Example 3
The link to skip repeated content does not have an accessible name.
```html
<!DOCTYPE html>
<html lang="en">
  <head><title></title></head>
  <body>
    <nav>
      <a href="#main-content"></a>
    </nav>
    <!-- Repeated Content -->
    <main id="main-content">Main Content</main>
  </body>
</html>
```

#### Failed Example 4
The link to skip repeated content does not reference a valid `id`.
```html
<!DOCTYPE html>
<html lang="en">
  <head><title></title></head>
  <body>
    <nav>
      <a href="#nowhere">Skip to main content</a>
    </nav>
    <!-- Repeated Content -->
    <main id="somewhere"></main>
  </body>
</html>
```

#### Failed Example 5
The link to skip repeated content is not visible, and is not included in the accessibility tree.
```html
<!DOCTYPE html>
<html lang="en">
  <head><title></title></head>
  <body>
    <nav>
      <a href="#main-content" style="display:none;">Skip to main content</a>
    </nav>
    <!-- Repeated Content -->
    <main id="main-content">Main Content</main>
  </body>
</html>
```

### Inapplicable

#### Inapplicable Example 1

The [document element](#https://dom.spec.whatwg.org/#document-element) of this [document](#https://dom.spec.whatwg.org/#concept-document) is not an `html` element.

```svg
<svg xmlns="http://www.w3.org/2000/svg">
  <title>This is an SVG</title>
</svg>
```
