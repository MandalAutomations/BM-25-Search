# Customizing how changed files appear on GitHub

To keep certain files from displaying in diffs by default, or counting toward the repository language, you can mark them with the linguist-generated attribute in a .gitattributes file.

Use a *.gitattributes* file to mark files that match a given "pattern" with the specified attributes. A *.gitattributes* file uses the same rules for matching as *.gitignore* files. For more information, see [PATTERN FORMAT](https://www.git-scm.com/docs/gitignore#_pattern_format) in the Git documentation.

1. Unless the *.gitattributes* file already exists, create a *.gitattributes* file in the root of the repository.
2. Use the `linguist-generated` attribute to mark or unmark paths that you would like to be ignored for the repository's language statistics and hidden by default in diffs.

   For example, to mark `search/index.json` as a generated file, add this line to *.gitattributes*:

   ```text
   search/index.json linguist-generated
   ```

   To unmark a file that would generally be considered *generated*, add this line to *.gitattributes*:

   ```text
   bootstrap.min.css -linguist-generated
   ```

## Further reading

* [Generated code](https://github.com/github-linguist/linguist/blob/main/docs/overrides.md#generated-code) in the Linguist documentation
* [Creating new files](/en/repositories/working-with-files/managing-files/creating-new-files)