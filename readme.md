# Polygon Coding Standards

This is a simple PHP Coding Standards ruleset based on the WordPress Coding Standards. It includes all the important rules defined in the WordPress Handbook.
By default, the WordPress Coding Standards includes WordPress-Core, WordPress-Docs and WordPress-Extra. This ruleset excludes a few minor rules like:

- Use Yoda conditions
- Missing translators comment
- Each PHP statement must be on a line by itself
- Line indented incorrectly; expected x tabs, found y
- Functions must not contain multiple empty lines in a row
- There must be exactly one empty line after the file comment

If you need to disable or exclude certain rules while writing code, use the following comments:

- // phpcs:ignore
- // phpcs:enable
- // phpcs:disable

To disable the coding standards for an entire file, add one of the comments below at the top of your file.

- // phpcs:ignoreFile
- // phpcs:ignoreFile -- reason to ignore
