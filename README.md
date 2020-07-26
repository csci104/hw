# Homework

This repository is private and should only be accessed by the student who owns it and course staff or professors.
Please do not share your code or copy other peoples', as it is always pretty obvious and will be caught by our plagiarism detection software.

## Getting Started

You might have noticed a couple extra files lying around this repository.
Here's a rundown of what they do.

- `.clang-format` provides some settings for `clang-format`, which is a tool you can use to automatically reformat your code.
  We've included some instructions on how to use it below.
  Feel free to page through the configuration file if you're interested in how it works.
- `.clang-tidy` provides settings for `clang-tidy`, which does semantic checks on C++ files.
  Just like for `clang-format`, we've included instructions on how to use this tool below.
- `.editorconfig` gives most IDEs some idea about how to handle whitespace in your code files.
  It also limits the charset to `utf8` to avoid any encoding bugs.
- `.gitignore` prevents files from being added to the index by git.
  Make sure you use this to avoid pushing things like compiled binaries and test files to keep your repository slim and ensure that graders can easily pick out what they need to grade.
  You can add a `.gitignore` file in any of this repository's subdirectories to add rules relative to that path.

## Formatting

`clang-format` is a utility built on top of the `clang` tooling that, among other things, visually restructures code based on a set of style guidelines.
**`clang-format` does not change what your code does or how it works**, instead managing things like spaces, newlines, brackets, and indentation.

You can invoke `clang-format` from the command line, and it comes installed out of the box on our [Docker container](https://github.com/csci104/docker).
We have already provided you with a set of rules, so running the utility within your homework repository is as easy as:

```
$ clang-format -i hw1/file.cpp
``` 

If you want to format multiple files in a directory, you can use wildcard operators:

```
# format all .cpp files in hw1/
$ clang-format -i hw1/*.cpp

# format all .cpp and .h files in hw1/ 
$ clang-format -i hw1/*.{h,cpp}
```

Lastly, you can use the double asterisk to recursively glob.
This is necessary when you also want to format files in subdirectories.

```
# format all .cpp and .h files in hw1/ and subdirectories
$ clang-format -i hw1/**/*.{h,cpp}
```

Please make sure you **format your code before submitting**. 
This ensures that graders can easily read and give you points for your work.
It will also prevent you from losing points for formatting in code review. 

## Linting

`clang-tidy` is another tool for analyzing and fixing your code, but instead of focusing on syntax, it deals with semantics.
In short, `clang-tidy` provides additional insights into your code.
For example, it can warn you about unsafe memory management, point out unused variables, and suggest more modern approaches for certain snippets.
Much like `clang-format`, you can invoke `clang-tidy` from the command line.
We recommend you use it one file at a time so that the output is more digestible:

```
# Get warnings about a single file
$ clang-tidy hw1/file.cpp --

# You can add arguments you'd pass to g++ after the --
$ clang-tidy hw1/file.cpp -- -I included/
```

Unlike `clang-format`, we don't require you to use `clang-tidy`.
Instead, we just offer it as a way for you to debug your assigment submissions.
Oftentimes, you'll find that heeding the warnings from `clang-tidy` will save you from bugs before you even find them.
