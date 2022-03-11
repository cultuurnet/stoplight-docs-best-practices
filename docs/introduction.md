# Introduction

Welcome to publiq's API design and documentation guidelines! 👋

This space is meant to share best practices that should be followed for every API that is developed within our organization.

Many of publiq's partners integrate with not only one, but multiple of our APIs. Additionally a lot of our own applications that are built by internal developers and/or external partners communicate with multiple of our APIs.

To **reduce the learning curve of integrators that work with multiple of our APIs**, we have agreed upon some standards for common functionality. These standards make it more predictable how our APIs work (*"learn once, apply everywhere"*). In some cases it might even be possible to re-use existing code for boilerplate functionality like authentication, error handling, etc in an integration.

Additionally, they **speed up development of our APIs** by reducing the time spent on bikeshedding over design decisions per API.

## Why do we not use standard *x*?

We try to follow industry standards where possible, but sometimes there are competing standards, or we have to deviate due to backward-compatibility reasons so we can align existing APIs with these standards.

## Why does API *x* not follow the standards?

Some APIs were built before these standards were agreed upon. When we add new standards, we try to look at existing APIs and make sure they are compatible with them or can be made compatible with them without too much effort. However this is not always possible, or the compatibility has yet to be added.
