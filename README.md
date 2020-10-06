# Codacy CPPCheck

[![Codacy Badge](https://api.codacy.com/project/badge/Grade/3bd4fdde0b9b43dd9aead3130d370c5d)](https://www.codacy.com/gh/codacy/codacy-cppcheck?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=codacy/codacy-cppcheck&amp;utm_campaign=Badge_Grade)
[![Build Status](https://circleci.com/gh/codacy/codacy-cppcheck.svg?style=shield&circle-token=:circle-token)](https://circleci.com/gh/codacy/codacy-cppcheck)

This is the docker engine we use at Codacy to have [CPPCheck](http://cppcheck.sourceforge.net) support.
You can also create a docker to integrate the tool and language of your choice!
Check the **Docs** section for more information.

## Usage

You can create the docker by doing:

```bash
sbt universal:stage graalvm-native-image:packageBin
docker build -t codacy-cppcheck .
```

The docker is ran with the following command:

```bash
docker run --rm -v $srcDir:/src -v $configFile:/.codacyrc codacy-cppcheck
```

### Generate Docs

1. Update the `ARG toolVersion` in `Dockerfile`
2. Run the documentation generator:

```bash
sbt doc-generator/run
```

## Docs

[Tool Developer Guide](https://support.codacy.com/hc/en-us/articles/207994725-Tool-Developer-Guide)

[Tool Developer Guide - Using Scala](https://support.codacy.com/hc/en-us/articles/207280379-Tool-Developer-Guide-Using-Scala)

## Test

For a faster development loop you can create a Docker image based on the JVM instead of creating a native-image:

```bash
sbt universal:stage
docker build -t codacy-cppcheck --target dev .
```

We use the [codacy-plugins-test](https://github.com/codacy/codacy-plugins-test) to test our external tools integration.
You can follow the instructions there to make sure your tool is working as expected.

## What is Codacy

[Codacy](https://www.codacy.com/) is an Automated Code Review Tool that monitors your technical debt, helps you improve your code quality, teaches best practices to your developers, and helps you save time in Code Reviews.

### Among Codacy’s features

- Identify new Static Analysis issues
- Commit and Pull Request Analysis with GitHub, BitBucket/Stash, GitLab (and also direct git repositories)
- Auto-comments on Commits and Pull Requests
- Integrations with Slack, HipChat, Jira, YouTrack
- Track issues in Code Style, Security, Error Proneness, Performance, Unused Code and other categories

Codacy also helps keep track of Code Coverage, Code Duplication, and Code Complexity.

Codacy supports PHP, Python, Ruby, Java, JavaScript, and Scala, among others.

### Free for Open Source

Codacy is free for Open Source projects.
