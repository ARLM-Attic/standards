---
Title: Coding Styles
---

Style is a very personal thing when it comes to developers. When a programmer is working alone, their file naturally follows their preferred style and formatting of code. However, when working with multiple people, having a common system of naming, formatting, and organization makes it easier to comprehend and merge code. Even something as simple as creating `diff` output is facilitated when everyone works with the same rules.

This project is not to document the One True Style for any language. It will never be that, simply because no one will ever agree what is the best to formatting and naming. However, this project does focus on how to format code that is intended to be included in the various projects for [Moonfire Games](http://mfgames.com/).

This is a living project. Styles change over time, both with the technology and the languages used. What works for one language (say underscore in variable names) doesn't work for another. Likewise, as the coding style for one language changes, the entire base will evolve.

# Common Style

Since we use multiple languages but the developers are the same, we have gradually come up with a common style for formatting all languages. This way, individual programming languages are listed as expectations to the common rules instead of duplicating the effort for every one.

* [Stanza Code Blocks](stanzas)
* [Acronyms and Abbreviations](acronyms)

# Specific Languages Styles

Every language has different preferred methods for organizing code. For example, in Perl we use lowercase variables with underscore infixes (some_variable_name) but in C#, the same variable would be in Camel Case (someVariableName). In these cases, use the common style with the specific language exceptions describing the differences.

* [C#](csharp)
* [Perl](perl)
* [Python](python)

# Settings

The other part of this project is to create a repository of settings files for programs that perform automated reformatting or stylistic checks. This way there is a centralized repository for formatting that can evolve with this guide.

# Reformatting Changes

Since this is an evolving standard, there are times when a code has drifted past the current standard. There are two ways of bringing a file up to the standard.

The first is to reformat as you go and only change the lines around where you are making changes. This makes it easy to do small bits, but if the reformatting is extensive then it can obscure the actual changes.

The preferred method is to have a separate, isolated check-in simply to reformat and bring the file up to standards. This makes it easier to review those changes with the knowledge that the code should not functionally change.

If given a choice, do a style reformat before functional changes to the code.

# Appendixes

* [Terminology](terminology)