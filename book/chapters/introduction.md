# Introduction

## About this book

I am writing this book because I find it easier to learn new technologies if the examples are in a language which I already know. For example, learning Test Driven Development is difficult as most of the books use Java as the examples, whereas I am primarily a PHP developer.

I also prefer to learn from books, rather than videos. I think it's a shame that technical books are not as popular as they used to be, either in paper or electronic form.

This book is currently a work in progress, and therefore may contain errors or missing chapters.

## Assumptions

Whilst this is an introductory book on Docker, I am making some assumptions about your knowledge, including:

 * You are familiar with PHP and use it as your primary development language.
 * You are comfortable with using the command line on Linux or macOS.
 * You are running a recent version of Linux or macOS, released within the last 2 years.
 * If you are running macOS, you have Homebrew installed.

I use the latest Ubuntu LTS (22.04) as my main development machine, and any examples are tested on that environment.

## Installing Docker

There are several ways you can install Docker, and I won't repeat all the instructions here. Instead, check the [Get Docker](https://docs.docker.com/get-docker/) pages on the official Docker website.

If you are running Ubuntu, I strongly recommend that you run an LTS release, as the upstream repositories do not support interim releases.

## Testing your installation

Once you have Docker installed, you can test it by running the 'hello world' image:

```bash
$ docker run hello-world
```

You should receive a message saying that your installation is working correctly.
