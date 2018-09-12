language: ruby

dist: trusty

sudo: required

branches:

  only:

    - master

    - auto

    - /^[\d.]+$/

    - /.+-stable$/

rvm:

  - 2.2.10

  - 2.3.7

  - 2.4.4

  - 2.5.1

  - ruby-head

env:

  - "TEST_TOOL=rubygems YAML=psych"

  - "TEST_TOOL=bundler RGV=master"

before_script:

  - util/ci before_script

script:

  - util/ci script

matrix:

  allow_failures:

    - rvm: ruby-head

      env: "TEST_TOOL=bundler RGV=master"
