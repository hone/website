---
title: Ember 2.12 and 2.13 Beta Released
author: Godfrey Chan, Brendan McLoughlin
tags: Releases
---

Today, the Ember project is releasing Ember.js, Ember Data and Ember CLI
version 2.12.0.

This also kicks off the 2.13 beta cycle for all sub-projects. We encourage our
community (especially addon authors) to help test these beta builds and report
any bugs before they are published as a final release in six weeks' time. The
[ember-try](https://github.com/ember-cli/ember-try) addon is a great way to
continuously test your projects against the latest Ember releases.

You can read more about our general release process here:

- [Release Dashboard](http://emberjs.com/builds/)
- [The Ember Release Cycle](http://emberjs.com/blog/2013/09/06/new-ember-release-process.html)
- [The Ember Project](http://emberjs.com/blog/2015/06/16/ember-project-at-2-0.html)
- [Ember LTS Releases](http://emberjs.com/blog/2016/02/25/announcing-embers-first-lts.html)

---

## Ember.js

Ember.js is the core framework for building ambitious web applications.

### Changes in Ember.js 2.12

The
2.12.0 release is an Ember.js Long-term support candidate. In six weeks, the 2.12.x series
will become the latest LTS release and six weeks after that the 2.8 LTS branch
will no longer receive bugfix patches.

For more information about Ember's LTS policies, see the
[announcement blog
post](http://emberjs.com/blog/2016/02/25/announcing-embers-first-lts.html) and
[builds page](http://emberjs.com/builds/).

Ember 2.12 implements the `factoryFor` API as described in [RFC #150](https://github.com/emberjs/rfcs/blob/master/text/0150-factory-for.md).
This public API replaces the intimate API of `_lookupFactory`, and additionally
discourages developers from setting properies on classes returned from the
container. For more information about this API see the [API
docs](http://emberjs.com/api/classes/ContainerProxyMixin.html#method_factoryFor)
and [`_lookupFactory` deprecation guide](http://emberjs.com/deprecations/v2.x/#toc_migrating-from-_lookupfactory-to-factoryfor).

Addon authors and others should consider if the
[ember-factory-for-polyfill](https://github.com/rwjblue/ember-factory-for-polyfill)
addon can help them avoid the deprecation warning for `_lookupFactory`.

#### Deprecations in Ember 2.12

- The `Ember.K` utility function is deprecated per [RFC #178](https://github.com/emberjs/rfcs/blob/master/text/0178-deprecate-ember-k.md).
  See the [deprecation guide](http://emberjs.com/deprecations/v2.x/#toc_code-ember-k-code)
  and pull request [#14751](https://github.com/emberjs/ember.js/pull/14751)
  for additional details.

- Arguments to the component lifecycle hooks of `didInitAttrs`, `didReceiveAttrs`, and `didUpdateAttrs`
  are deprecated. These arguments were private and undocumented. Please see
  [RFC #191](https://github.com/emberjs/rfcs/blob/master/text/0191-deprecate-component-lifecycle-hook-args.md)
  for further context and discussion.
  Please note that
  this only deprecates the usage of the arguments passed to this hook, not the
  hooks themselves. See pull request [#14711](https://github.com/emberjs/ember.js/pull/14711)
  for additional details.

For more details on the changes in Ember.js 2.12, please review the
[Ember.js 2.12.0 release page](https://github.com/emberjs/ember.js/releases/tag/v2.12.0).

### Upcoming Changes in Ember.js 2.13

Building on the addition of `featureFor` in Ember 2.12, Ember 2.13 will change
the way dependency injection is implemented in the framework. Until 2.12,
dependencies were injected onto an instance using `extend` to create a subclass.
This created an excessive number of subclasses during the execution of an
application. In Ember 2.13 injections will be passed to an object via `create`
when it is instantiated. This results in a notable performance improvement
that is grows in impact with the complexity of an application.

See [RFC #150](https://github.com/emberjs/rfcs/blob/master/text/0150-factory-for.md)
and pull request [#14360](https://github.com/emberjs/ember.js/pull/14360) for
more details about this change.

In addition to this and other improvements, several changes arising
from the [RFC](https://github.com/emberjs/rfcs) process have been implemented:

- [RFC issue #146](https://github.com/emberjs/rfcs/issues/146) advocated for the
  addition of `resumeTest` as a compliment to `pauseTest`. This was implemented
  in [#13663](https://github.com/emberjs/ember.js/pull/13663).
- [RFC #186](https://github.com/emberjs/rfcs/blob/master/text/0186-track-unique-history-location-state.md)
  describes the addition of `uuid` as a property on `HistoryLocation` adapters
  for the router. This adition makes it possible to track scroll locations
  to a point in browsing history. See pull request [#14011](https://github.com/emberjs/ember.js/pull/14011)
  for more details.

For more details on the upcoming changes in Ember.js 2.13, please review the
[Ember.js 2.13.0-beta.1 release page](https://github.com/emberjs/ember.js/releases/tag/v2.13.0-beta.1).

---

## Ember Data

Ember Data is the official data persistence library for Ember.js applications.

### Changes in Ember Data 2.12


#### Deprecations in Ember Data 2.12


### Upcoming changes in Ember Data 2.13

#### Deprecations in Ember Data 2.13

---

## Ember CLI

Ember CLI is the command line interface for managing and packaging Ember.js
applications.

### Upgrading Ember CLI

You may upgrade Ember CLI separately from Ember.js and Ember Data! To upgrade
your projects using `yarn` run:

```
yarn upgrade ember-cli
```

To upgrade your projects using `npm` run:

```
npm install --save-dev ember-cli
```

After running the
upgrade command run `ember init` inside of the project directory to apply the
blueprint changes. You can preview those changes for [applications](https://github.com/ember-cli/ember-new-output/compare/v2.11.0...v2.12.0)
and [addons](https://github.com/ember-cli/ember-addon-output/compare/v2.11.0...v2.12.0).

### Changes in Ember CLI 2.12

#### Other Notable Changes

For more details on the changes in Ember CLI 2.12 and detailed upgrade
instructions, please review the [Ember CLI 2.12.0 release page](https://github.com/ember-cli/ember-cli/releases/tag/v2.12.0).

### Upcoming Changes in Ember CLI 2.13

#### Other Notable Changes

For more details on the changes in Ember CLI 2.13.0-beta.1 and detailed upgrade
instructions, please review the [Ember CLI 2.13.0-beta.1 release page](https://github.com/ember-cli/ember-cli/releases/tag/v2.13.0-beta.1).

## Thank You!

As a community-driven open-source project with an ambitious scope, each of
these releases serve as a reminder that the Ember project would not have been
possible without your continued support. We are extremely grateful to our
contributors for their efforts.
