# Custom patterns reference

Use specific regular expression syntax to define accurate custom patterns for secret scanning.

## Regular expression library for custom patterns

Secret scanning custom patterns are defined using the [Hyperscan library](https://github.com/intel/hyperscan) and only support Hyperscan regex constructs, which are a subset of PCRE syntax. Hyperscan option modifiers are not supported. For more information on Hyperscan pattern constructs, see [Pattern support](https://intel.github.io/hyperscan/dev-reference/compilation.html#pattern-support) in the Hyperscan documentation.

## Syntax for manually defining custom patterns

The **More options <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-chevron-down" aria-label="chevron-down" role="img"><path d="M12.78 5.22a.749.749 0 0 1 0 1.06l-4.25 4.25a.749.749 0 0 1-1.06 0L3.22 6.28a.749.749 0 1 1 1.06-1.06L8 8.939l3.72-3.719a.749.749 0 0 1 1.06 0Z"></path></svg>** section in the UI helps you write regular expressions manually.

* **Secret format:** an expression that describes the format of the secret itself.
* **Before secret:** an expression that describes the characters that come before the secret. By default, this is set to `\A|[^0-9A-Za-z]` which means that the secret must be at the start of a line or be preceded by a non-alphanumeric character.
* **After secret:** an expression that describes the characters that come after the secret. By default, this is set to `\z|[^0-9A-Za-z]` which means that the secret must be followed by a new line or a non-alphanumeric character.
* **Additional match requirements:** one or more optional expressions that the secret itself must or must not match.

For simple tokens you will usually only need to specify a secret format. The other fields provide flexibility so that you can specify more complex secrets without creating complex regular expressions.

### Example custom pattern

A company has an internal token with five characteristics. They use the different fields to specify how to identify tokens as follows:

| **Characteristic** | **Field and regular expression** |
|----------------|------------------------------|
| Length between 5 and 10 characters | Secret format: `[$#%@AA-Za-z0-9]{5,10}` |
| Does not end in a `.` | After secret: `[^\.]` |
| Contains numbers and uppercase letters | Additional requirements: secret must match `[A-Z]` and `[0-9]` |
| Does not include more than one lowercase letter in a row | Additional requirements: secret must not match `[a-z]{2,}` |
| Contains one of `$%@!` | Additional requirements: secret must match `[$%@!]` |

These tokens would match the custom pattern described above:

```shell
a9@AAfT!         # Secret string match: a9@AAfT
ee95GG@ZA942@aa  # Secret string match: @ZA942@a
a9@AA!ee9        # Secret string match: a9@AA
```

These strings would not match the custom pattern described above:

```shell
a9@AA.!
a@AAAAA
aa9@AA!ee9
aAAAe9
```

## Limits

Secret scanning supports up to 500 custom patterns for each organization or enterprise account, and up to 100 custom patterns per repository.