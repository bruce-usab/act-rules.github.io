---
id: b40fd1
name: HTML page has a main landmark
rule_type: atomic
description: |
  This rule checks that each page has an element with a semantic role of `main`
accessibility_requirements:
input_aspects:
	- DOM Tree
	- CSS styling
authors:
	- Jean-Yves Moyen
	- Anne Thyme Nørregard
---

## Applicability

This rule applies to any [document](#https://www.w3.org/TR/dom/#concept-document) where the [document element](#https://www.w3.org/TR/dom/#document-element) is an HTML `html` element.

## Expectations

The [document element](https://www.w3.org/TR/dom/#document-element) has at least one [descendant](https://www.w3.org/TR/dom41/#concept-tree-descendant) in the [flat tree](https://drafts.csswg.org/css-scoping/#flat-tree) with a [semantic role][#semantic-role] of [`main`](https://www.w3.org/TR/wai-aria-1.1/#main).

**Note**: Authors SHOULD not use more than one element with a [semantic role](#semantic-role) of [`main`](https://www.w3.org/TR/wai-aria-1.1/#main). This is, however, a not a requirement for this rule nor for technique [ARIA11: Using ARIA landmarks to identify regions of a page](https://www.w3.org/WAI/WCAG21/Techniques/aria/ARIA11).

## Assumptions

_There are currently no assumptions_

## Accessibility Support

_There are no major accessibility support issues known for this rule._

## Background

- [ARIA11: Using ARIA landmarks to identify regions of a page](https://www.w3.org/WAI/WCAG21/Techniques/aria/ARIA11)
- [ARIA Landmarks Example](https://www.w3.org/TR/wai-aria-practices/examples/landmarks/index.html)

## Test Cases

### Passed

### Failed

### Inapplicable