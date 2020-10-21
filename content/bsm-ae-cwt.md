---
title: "LHC autoencoder neural network for wavelet transform"
date: 2019-12-10
slug: "bsm-ae-lhc"
description: "Generating Signals, Backgrounds and Wavelets"
keywords: ["Python", "CWT"]
draft: false
tags: ["Python", "CWT"]
math: true
toc: false
---

This is a short technical tutorial to get quickly into configuring signals, backgrounds and wavelets
using the [Signal Generator](https://github.com/karopastal/signal_generator). Make sure before starting 
that you have completed the project setup/update as presented in the project's [README](https://github.com/karopastal/signal_generator/blob/master/README.md).

# up and running

Lets run the management app: 

```bash
$ make web
```

**Visit the management app: http://127.0.0.1:5000/**

As you can see under the signals, background and wavelets tabs there is a configuration that is presented by default. Using the 
interface you can edit, delete and add new ones. Once you are done and want to save the configuration you shall use the **`sessions`**
option that will be presented in the next section.

## sessions
A session is a way to save the current state of the [managment app](http://127.0.0.1:5000/). <br/>
**NOTE**: the sessions are saved as `.json` files. the **`NAME`** argument accepts only the session's name **without** the `.json` suffix.

### listing
Lets run the following command in order to list the current saved sessions:
```shell script
  $ make list-sessions
```
This should print:

```shell script
classifier_toy_dataset.json  default_example_session.json
```

Those are the current sessions available. As mentioned before the configuration that presented by default with the
[managment app](http://127.0.0.1:5000/) called the `default_example_session`.

### loading
Lets try to load the `clasifier_toy_dataset` session:

```s
  $ make load-session NAME=clasifier_toy_dataset
```

Now refresh the [managment app](http://127.0.0.1:5000/), as you can see we set the state to the `clasifier_toy_dataset`!

### saving

Visit the [managment app](http://127.0.0.1:5000/) and change the configuration by adding for example a new signal.
Now we want to save this new configuration in a separate session:

```bash
  $ make save-session NAME=new_configuration
```

Lets try to list again the sessions and we will get that:

```s
  $ make list-sessions
```

This should print:

```s
classifier_toy_dataset.json  default_example_session.json new_configuration.json
```

### deleting

```s
  $ make delete-session NAME=new_configuration
```

Lets check that `new_configuration` is no longer available:

```s
  $ make list-sessions
```

This should print:

```s
classifier_toy_dataset.json  default_example_session.json
```

Now you have all the functionality needed to list, save, load and delete sessions!