# Agrigento

## Research paper

We present the findings of this work in the following research paper:

**Obfuscation-Resilient Privacy Leak Detection for Mobile Apps Through Differential Analysis**  
Andrea Continella, Yanick Fratantonio, Martina Lindorfer, Alessandro Puccetti, Ali Zand, Christopher Kruegel, Giovanni Vigna.
*In Proceedings of the ISOC Network and Distributed System Security Symposium (NDSS), February 2017*

[[PDF](https://conand.me/publications/continella-agrigento-2017.pdf)]

If you use *Agrigento* in a scientific publication, we would appreciate citations using this **Bibtex** entry:
``` tex
@InProceedings{continella17:agrigento,
  author = {Andrea Continella and Yanick Fratantonio and Martina Lindorfer and Alessandro Puccetti and Ali Zand and Christopher Kruegel and Giovanni Vigna},
  title = {{Obfuscation-Resilient Privacy Leak Detection for Mobile Apps Through Differential Analysis}},
  booktitle = {Proceedings of the ISOC Network and Distributed System Security Symposium (NDSS)},
  month = {February},
  year = {2020},
  address = {San Diego, CA}
}
```

## Introduction

Agrigento is based on black-box differential analysis, and it works in two steps: first, it establishes a baseline of the network behavior of an app; then, it modifies sources of private information, such as the device ID and location, and detects privacy leaks by observing deviations in the resulting network traffic. The basic concept of black-box differential analysis is not novel, but, unfortunately, it is not practical enough to precisely analyze modern mobile apps. In fact, their network traffic contains many sources of non-determinism, such as random identifiers, timestamps, and server-assigned session identifiers, which, when not handled properly, cause too much noise to correlate output changes with input changes.
The main contribution of this work is to make black-box differential analysis practical when applied to modern Android apps.

Agrigento is able to eliminate the different sources of non-determinism by intercepting calls from the app to certain Android API calls and recording their return values, and in
some cases replacing them (either by replaying previously seen values or by returning constant values).

* Agrigento records the timestamps generated during the first run of each app, and replays the same values in the further runs.
* It records the random identifiers (UUID) generated by the app.
* It records the plaintext and ciphertext values whenever the app performs encryption.
* The instrumented environment sets a fixed seed for all random number generation functions.
* It replaces the values of system-related performance measures (e.g., free memory, available storage space) with a set of constants.

## Dataset release

In the spirit of open science we are happy to release our datasets to the community. If you are interested in getting access to our data, send us an email ([acontinella@iseclab.org](mailto:acontinella@iseclab.org), [yanick@cs.ucsb.edu](mailto:yanick@cs.ucsb.edu), [martina@iseclab.org](mailto:martina@iseclab.org)).
