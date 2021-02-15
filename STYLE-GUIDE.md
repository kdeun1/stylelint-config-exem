# EXEM CSS 스타일 가이드

## Example
```css
@import url(x.css);
@import url(y.css);

/**
* Multi-line comment
*/

.selector-1,
.selector-2,
.selector-3[type='text'] {
  display: block;
  box-sizing: border-box;
  background: linear-gradient(#FFFFFF, rgba(0, 0, 0, 0.8));
  color: #333333;
}

.selector-a,
.selector-b:not(:first-child) {
  top: calc(calc(1em * 2) / 3);
  padding: 10px !important;
}

.selector-x { width: 10%; }
.selector-y { width: 20%; }
.selector-z { width: 30%; }

/* Single-line comment */

@media (min-width >= 60em) {
.selector {
  /* Flush to parent comment */
  transform: translate(1, 1) scale(3);
}
}

@media (orientation: portrait), projection and (color) {
.selector-i + .selector-ii {
  background: color(rgb(0, 0, 0) lightness(50%));
  font-family: helvetica, 'arial black', sans-serif;
}
}

/* Flush single line comment */
.selector {
  height: 10rem;
  margin: 10px;
  margin-bottom: 5px;
  background-image:
    repeating-linear-gradient(
      -45deg,
      transparent,
      #FFFFFF 25px,
      rgba(255, 255, 255, 1) 50px
    );
  box-shadow:
    0 1px 1px #000000,
    0 1px 0 #FFFFFF,
    2px 2px 1px 1px #CCCCCC inset;
}

@media
  screen and (min-resolution: 192dpi),
  screen and (min-resolution: 2dppx) {
    /* Flush nested single line comment */
    .selector::after {
    background-image: url(x.svg);
    content: '→';
  }
}
```
```scss
@import 'path/x';
@import 'path/y.css';

$action-color: #4285F4;
$reset-color: #CDDC39;

@mixin mixin-source() {
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

%selector-source {
  box-sizing: border-box;
  width: 100%;
  padding: 16px 0;
  border-top: 1px rgba(#000000, 0.12) solid;

  &:hover { border: 2px rgba(#000000, 0.5) solid; }
}

.selector-x {
  @extend %selector-source;

  color: $action-color;

  @include mixin-source;
}

.selector-y {
  @extend %selector-source;

  color: $reset-color;
}
```

## Documentation

### Plugins
- [`stylelint-order`](https://github.com/hudochenkov/stylelint-order)
- [`stylelint-scss`](https://github.com/kristerkari/stylelint-scss)

### Configured lints
아래는 stylelint-config-exem에서 적용하는 stylelint 규칙입니다.

**at-rule**
- [`at-rule-empty-line-before`](https://stylelint.io/user-guide/rules/at-rule-empty-line-before)
    ```
     [
      always,
      {
        except: [blockless-after-same-name-blockless, first-nested],
        ignore: [after-comment],
      },
    ]
    ```
- [`at-rule-name-case`](https://stylelint.io/user-guide/rules/at-rule-name-case): lower
- [`at-rule-name-space-after`](https://stylelint.io/user-guide/rules/at-rule-name-space-after): always-single-line
- [`at-rule-semicolon-newline-after`](https://stylelint.io/user-guide/rules/at-rule-semicolon-newline-after): always
- [`at-rule-no-unknown`](https://stylelint.io/user-guide/rules/at-rule-no-unknown): null

**block**
- [`block-closing-brace-empty-line-before`](https://stylelint.io/user-guide/rules/block-closing-brace-empty-line-before): never
- [`block-closing-brace-newline-after`](https://stylelint.io/user-guide/rules/block-closing-brace-newline-after): always
- [`block-closing-brace-newline-before`](https://stylelint.io/user-guide/rules/block-closing-brace-newline-before): always-multi-line
- [`block-closing-brace-space-before`](https://stylelint.io/user-guide/rules/block-closing-brace-space-before): always-single-line
- [`block-opening-brace-newline-after`](https://stylelint.io/user-guide/rules/block-opening-brace-newline-after): always-multi-line
- [`block-opening-brace-space-after`](https://stylelint.io/user-guide/rules/block-opening-brace-space-after): always-single-line
- [`block-opening-brace-space-before`](https://stylelint.io/user-guide/rules/block-opening-brace-space-before): always
- [`color-hex-case`](https://stylelint.io/user-guide/rules/color-hex-case): upper
- [`color-hex-length`](https://stylelint.io/user-guide/rules/color-hex-length): long  

**comment**
- [`comment-empty-line-before`](https://stylelint.io/user-guide/rules/comment-empty-line-before):
    ```
    [
      always,
      {
        except: [first-nested],
        ignore: [stylelint-commands],
      },
    ]
    ```
- [`comment-whitespace-inside`](https://stylelint.io/user-guide/rules/comment-whitespace-inside): always  

**custom-property**
- [`custom-property-empty-line-before`](https://stylelint.io/user-guide/rules/custom-property-empty-line-before):
    ``` 
    [
      always,
      {
        except: [after-custom-property, first-nested],
        ignore: [after-comment, inside-single-line-block],
      },
    ]
    ```

**declaration**
- [`declaration-bang-space-after`](https://stylelint.io/user-guide/rules/declaration-bang-space-after): never
- [`declaration-bang-space-before`](https://stylelint.io/user-guide/rules/declaration-bang-space-before): always
- [`declaration-block-semicolon-newline-after`](https://stylelint.io/user-guide/rules/declaration-block-semicolon-newline-after): always-multi-line
- [`declaration-block-semicolon-space-after`](https://stylelint.io/user-guide/rules/declaration-block-semicolon-space-after): always-single-line
- [`declaration-block-semicolon-space-before`](https://stylelint.io/user-guide/rules/declaration-block-semicolon-space-before): never
- [`declaration-block-single-line-max-declarations`](https://stylelint.io/user-guide/rules/declaration-block-single-line-max-declarations): 1
- [`declaration-block-trailing-semicolon`](https://stylelint.io/user-guide/rules/declaration-block-trailing-semicolon): always
- [`declaration-block-no-duplicate-properties`](https://stylelint.io/user-guide/rules/declaration-block-no-duplicate-properties): true
- [`declaration-colon-newline-after`](https://stylelint.io/user-guide/rules/declaration-colon-newline-after): always-multi-line
- [`declaration-colon-space-after`](https://stylelint.io/user-guide/rules/declaration-colon-space-after): always-single-line
- [`declaration-colon-space-before`](https://stylelint.io/user-guide/rules/declaration-colon-space-before): never
- [`declaration-empty-line-before`](https://stylelint.io/user-guide/rules/declaration-empty-line-before):
    ``` 
    [
      always,
      {
        except: [after-declaration, first-nested],
        ignore: [after-comment, inside-single-line-block],
      },
    ]
    ```

**function**
- [`function-comma-newline-after`](https://stylelint.io/user-guide/rules/function-comma-newline-after): always-multi-line
- [`function-comma-space-after`](https://stylelint.io/user-guide/rules/function-comma-space-after): always-single-line
- [`function-comma-space-before`](https://stylelint.io/user-guide/rules/function-comma-space-before): never
- [`function-max-empty-lines`](https://stylelint.io/user-guide/rules/function-max-empty-lines): 0
- [`function-name-case`](https://stylelint.io/user-guide/rules/function-name-case): lower
- [`function-parentheses-newline-inside`](https://stylelint.io/user-guide/rules/function-parentheses-newline-inside): always-multi-line
- [`function-parentheses-space-inside`](https://stylelint.io/user-guide/rules/function-parentheses-space-inside): never-single-line
- [`function-whitespace-after`](https://stylelint.io/user-guide/rules/function-whitespace-after): always  

**general**
- [`indentation`](https://stylelint.io/user-guide/rules/indentation): 2
- [`length-zero-no-unit`](https://stylelint.io/user-guide/rules/length-zero-no-unit): true
- [`max-empty-lines`](https://stylelint.io/user-guide/rules/max-empty-lines): 1
- [`max-nesting-depth`](https://stylelint.io/user-guide/rules/max-nesting-depth): 3
- [`no-eol-whitespace`](https://stylelint.io/user-guide/rules/no-eol-whitespace): true
- [`no-missing-end-of-source-newline`](https://stylelint.io/user-guide/rules/no-missing-end-of-source-newline): true  

**media**  
- [`media-feature-colon-space-after`](https://stylelint.io/user-guide/rules/media-feature-colon-space-after): always
- [`media-feature-colon-space-before`](https://stylelint.io/user-guide/rules/media-feature-colon-space-before): never
- [`media-feature-name-case`](https://stylelint.io/user-guide/rules/media-feature-name-case): lower
- [`media-feature-parentheses-space-inside`](https://stylelint.io/user-guide/rules/media-feature-parentheses-space-inside): never
- [`media-feature-range-operator-space-after`](https://stylelint.io/user-guide/rules/media-feature-range-operator-space-after): always
- [`media-feature-range-operator-space-before`](https://stylelint.io/user-guide/rules/media-feature-range-operator-space-before): always
- [`media-query-list-comma-newline-after`](https://stylelint.io/user-guide/rules/media-query-list-comma-newline-after): always-multi-line
- [`media-query-list-comma-space-after`](https://stylelint.io/user-guide/rules/media-query-list-comma-space-after): always-single-line
- [`media-query-list-comma-space-before`](https://stylelint.io/user-guide/rules/media-query-list-comma-space-before): never  

**number**
- [`number-leading-zero`](https://stylelint.io/user-guide/rules/number-leading-zero): always
- [`number-no-trailing-zeros`](https://stylelint.io/user-guide/rules/number-no-trailing-zeros): true  

**property**
- [`property-case`](https://stylelint.io/user-guide/rules/property-case): lower  

**scss**
- [`scss/at-extend-no-missing-placeholder`](https://github.com/kristerkari/stylelint-scss/blob/master/src/rules/at-extend-no-missing-placeholder/README.md): true
- [`scss/at-function-pattern`](https://github.com/kristerkari/stylelint-scss/blob/master/src/rules/at-function-pattern/README.md): ^[a-z]+([a-z0-9-_]+[a-z0-9]+)?$
- [`scss/at-import-no-partial-leading-underscore`](https://github.com/kristerkari/stylelint-scss/blob/master/src/rules/at-import-no-partial-leading-underscore/README.md): true
- [`scss/at-import-partial-extension-blacklist`](https://github.com/kristerkari/stylelint-scss/blob/master/src/rules/at-import-partial-extension-blacklist/README.md): [scss]
- [`scss/at-mixin-pattern`](https://github.com/kristerkari/stylelint-sat-mixin-patternd): ^[a-z]+([a-z0-9-_]+[a-z0-9]+)?$
- [`scss/at-rule-no-unknown`](https://github.com/kristerkari/stylelint-scss/blob/master/src/rules/scss/at-rule-no-unknown/README.md): true
- [`scss/dollar-variable-colon-space-after`](https://github.com/kristerkari/stylelint-scss/blob/master/src/rules/scss/dollar-variable-colon-space-after/README.md): always
- [`scss/dollar-variable-colon-space-before`](https://github.com/kristerkari/stylelint-scss/blob/master/src/rules/scss/dollar-variable-colon-space-before/README.md): never
- [`scss/dollar-variable-pattern`](https://github.com/kristerkari/stylelint-scss/blob/master/src/rules/scss/dollar-variable-pattern/README.md): ^[_]?[a-z]+([a-z0-9-_]+[a-z0-9]+)?$
- [`scss/percent-placeholder-pattern`](https://github.com/kristerkari/stylelint-scss/blob/master/src/rules/scss/percent-placeholder-pattern/README.md): ^[a-z]+([a-z0-9-_]+[a-z0-9]+)?$
- [`scss/selector-no-redundant-nesting-selector`](https://github.com/kristerkari/stylelint-scss/blob/master/src/rules/scss/selector-no-redundant-nesting-selector/README.md): true  

**selector**
- [`selector-attribute-brackets-space-inside`](https://stylelint.io/user-guide/rules/selector-attribute-brackets-space-inside): never
- [`selector-attribute-operator-space-after`](https://stylelint.io/user-guide/rules/selector-attribute-operator-space-after): never
- [`selector-attribute-operator-space-before`](https://stylelint.io/user-guide/rules/selector-attribute-operator-space-before): never
- [`selector-combinator-space-after`](https://stylelint.io/user-guide/rules/selector-combinator-space-after): always
- [`selector-combinator-space-before`](https://stylelint.io/user-guide/rules/selector-combinator-space-before): always
- [`selector-descendant-combinator-no-non-space`](https://stylelint.io/user-guide/rules/selector-descendant-combinator-no-non-space): true
- [`selector-list-comma-newline-after`](https://stylelint.io/user-guide/rules/selector-list-comma-newline-after): always
- [`selector-list-comma-space-before`](https://stylelint.io/user-guide/rules/selector-list-comma-space-before): never
- [`selector-max-empty-lines`](https://stylelint.io/user-guide/rules/selector-max-empty-lines): 0
- [`selector-max-compound-selectors`](https://stylelint.io/user-guide/rules/selector-max-compound-selectors): 3
- [`selector-pseudo-class-case`](https://stylelint.io/user-guide/rules/selector-pseudo-class-case): lower
- [`selector-pseudo-class-parentheses-space-inside`](https://stylelint.io/user-guide/rules/selector-pseudo-class-parentheses-space-inside): never
- [`selector-pseudo-element-case`](https://stylelint.io/user-guide/rules/selector-pseudo-element-case): lower
- [`selector-pseudo-element-colon-notation`](https://stylelint.io/user-guide/rules/selector-pseudo-element-colon-notation): double
- [`selector-type-case`](https://stylelint.io/user-guide/rules/selector-type-case): lower
- [`selector-no-qualifying-type`](https://stylelint.io/user-guide/rules/selector-no-qualifying-type): true  

**string**
- [`string-quotes`](https://stylelint.io/user-guide/rules/string-quotes): single
- [`unit-case`](https://stylelint.io/user-guide/rules/unit-case): lower  

**value**
- [`value-keyword-case`](https://stylelint.io/user-guide/rules/value-keyword-case): lower
- [`value-list-comma-newline-after`](https://stylelint.io/user-guide/rules/value-list-comma-newline-after): always-multi-line
- [`value-list-comma-space-after`](https://stylelint.io/user-guide/rules/value-list-comma-space-after): always-single-line
- [`value-list-comma-space-before`](https://stylelint.io/user-guide/rules/value-list-comma-space-before): never
- [`value-list-max-empty-lines`](https://stylelint.io/user-guide/rules/value-list-max-empty-lines): 0
