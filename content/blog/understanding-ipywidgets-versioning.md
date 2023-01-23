---
title: Understanding ipywidgets versioning
description: >-
  An overview of how versioning works in ipywidgets from the perspective on a
  front end client like Thebe
date: '2022-09-28T08:29:29.941Z'
name: understanding-ipywidgets-versioning
oxa: oxa:DOHMeg040aVXqR51yjBy/RidjGHQ3DxCKVMqL9nHb
short_title: ''
tags:
  - ipywidgets
  - jupyter
  - code
thumbnail: thumbnails/understanding-ipywidgets-versioning.png
---

+++ {"oxa":"oxa:DOHMeg040aVXqR51yjBy/vg8SVCDPURraDyqyTW3O.1","tags":[]}

`ipywidgets` enable interactive UI components in the browser that are linked to a running python session. There needs to be some alignment between the **major** versions of the ipywidgets packages in the python kernel and in use on the frontend.

When using `ipywidgets` in Jupyter, you only need to think about this alignment in terms of the version of the notebook extension that you install, and even less so now that Jupyter Lab extensions are automatically installed. If you are using a library like [thebe](https://github.com/executablebooks/thebe) or developing you own Jupyter client, you need to know about these versions.

```{figure} images/DOHMeg040aVXqR51yjBy-3iCLSMAbsWAb8e4GVCWV-v1.png
:name: wDs7POpJZe
:align: center
:width: 100%
```

## Release Versions

At the time of writing `ipywidgets@v8.0.2` had just been released - so there are two major versions that are likely to be in use in the wild `v7.x` (most likely `v7.7.x`) and `v8` as it is adopted.

## Under the hood versions

There are two version numbers baked into the `ipywidgets` code, which are distinct from both package and release version numbers. These are shown below and relate to the underlying `ipywidgets` protocol and schema versions in use in any particular release.

```typescript
// https://github.com/jupyter-widgets/ipywidgets/blob/master/packages/base/src/version.ts
export var JUPYTER_WIDGETS_VERSION = '1.2.0';
export var PROTOCOL_VERSION = '2.1.0';

// https://github.com/jupyter-widgets/ipywidgets/blob/master/packages/controls/src/version.ts
/**
 * The version of the Jupyter controls widget attribute spec that this package
 * implements.
 */
export const JUPYTER_CONTROLS_VERSION = '2.0.0';


// https://github.com/jupyter-widgets/ipywidgets/blob/master/packages/output/src/output.ts
export const OUTPUT_WIDGET_VERSION = '1.0.0';


//https://github.com/jupyter-widgets/ipywidgets/blob/master/packages/base-manager/src/manager-base.ts
/**
 * The supported version for the control comm channel.
 */
export const CONTROL_COMM_PROTOCOL_VERSION = '1.0.0';
```

The values in the code above are those for the `8.0.0` release make in September 2022.

When `ipywidgets` are used with `jupyter lab` they are installed during the installation of the overall python package as the extension is automatically installed in `lab`. So for that frontend, keeping in sync with the server version is trivial.

More generally for frontends like thebe though we either need to build against a specific **major** version of `ipywidgets` or be prepared to dynamically load the **right** `js` packages.

What are the right `js` packages?

## Package Versions

So we have release versions and under the hood versions of components. In between these two, from a front end client perspective anyways, we have versions of the following packages to consider:

```json
{
 	"@jupyter-widgets/base": "^6.0.1",
    "@jupyter-widgets/controls": "^5.0.1",
    "@jupyter-widgets/output": "^6.0.1",
    "@jupyter-widgets/html-manager": "^1.0.3",
    "@jupyter-widgets/jupyterlab-manager": "^5.0.3"
}
```

The packages shown above align with the `v8.0.x` release. For `v7.7.1` the versions are shown below.

```json
{
	"@jupyter-widgets/base": "^4.1.1",
    "@jupyter-widgets/controls": "^3.1.1",
    "@jupyter-widgets/output": "^4.1.1",
    "@jupyter-widgets/html-manager": "^0.20.2",
    "@jupyter-widgets/jupyterlab-manager": "^3.1.1"  
}
```

So a front end client should align to these package version when targeting a specific `ipywidgets` major release version.

