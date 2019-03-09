# Sustainability requirements for `tensorflow/addons`

| Status        | Proposed       |
:-------------- |:---------------------------------------------------- |
| **Author(s)** | Paige Bailey (webpaige@google.com), Sean Morgan (seanmorgan@outlook.com) |
| **Sponsor**   | Karmel Allison (karmel@google.com)                 |
| **Updated**   | 2019-03-08                                           |

## Objective

TensorFlow Addons is a repository of contributions that conform to well-established API patterns, but implement new functionality not available in core TensorFlow. For TensorFlow Addons to support [code that is moved from `tf.contrib to addons](https://github.com/tensorflow/community/blob/ef626896f30130dfc3b5e75126c94624b689a943/rfcs/20181214-move-to-addons.md#code-to-be-moved-from-tfcontrib-to-addons), as well as new operations, requirements for maintaining and retiring those modules must be defined and enforced.

This document details requirements and responsibilities for owning a module that is included in TensorFlow Addons.

## Motivation

In this RFC, we are soliciting discussion regarding Addons module maintainership. This RFC discussion will help the SIG Addons team determine appropriate roles and responsibilities for proxy maintainers.

## Design Proposal 

### Privileges and responsibitilies of proxied maintainers

Proxy maintainers may add new packages to `tensorflow/addons`, provided they are willing to maintain them afterwards. In order to do so, 

### How to become a proxied maintainer

#### Adding a new package

The SIG Addons core team will review the submitted files (_TBD: tests, contact information, etc._) and help bring them to the top quality. Once the package is ready, it will be merged and the relevant bugs will be closed (if there are any).

Please note that we reserve the right to reject new packages, especially if they would otherwise qualify for removal per our quality standards. Example reasons for rejection include:

* Having known major bugs or security issues.
* Duplicating functionality in the TensorFlow core API.
* Having deprecated upstream dependencies.
* Failling to obtain an appropriate code review.
* Having no general usefulness for TensorFlow users.

#### Taking over an existing package

Proxy maintainers may also co-maintain existing TensorFlow Addons packages. If a potential maintainer chooses to do so, there are a few things to consider first:

* If the package has an existing maintainer, the potential maintainer must community with them first. The existing maintainer would need to approve the co-maintainer role, and might give the potential maintainer a specific task to do first.

* If the package has major bugs (especially if the quality of bugs would recommend it for removal), the potential maintainer will need to provide fixes for at least some of them before their request is approved. 

* If you do not have a few prior contributions as a proxied maintainer and neither of the above applied, you will need to provide some meaningful update to the ebuild. This usually involves bump to a newer EAPI, QA fixes, bug fixes — anything that could prove that you can write ebuilds. When in doubt, contact us first and we'll try to find you something to do.

* Once you've established what needs to be done, please submit a commit adding yourself to metadata.xml as a (co-)maintainer, followed by the specific commits required to fix the package and/or prove your skills.

#### Readding a removed package

If a potential maintainer wishes to readd a package that has been removed from TensorFlow Addons, they must explicitly note that on their submission. The procedure for readding a package combines the requirements for adding a new package and taking over an unmaintained package. Thus, a potential maintainer would be required to:

* Submit a good quality build (either a new one or based on the old one).
* Fix the issues that prompted the package removal in the first place.

### Being a proxied maintainer

#### Testing

#### Resolving bugs

Proxy maintainers would be expected to handle bugs against packages they own themselves. This includes resolving them once their fix is merged by a proxy maintainer, or rejecting them based on their own judgment. Proxy maintainers must repond to issues within 48 hours, and resolve them within 30 days in order for their packages to remain in TensorFlow Addons.

### Retiring from proxy maintainership

If a proxy maintainer decides that they no longer wish to maintain one or more of their packages, they must commit to the following procedure:

* If the proxy maintainer is the last maintainer of some of the packages (not counting proxy-maint project), please send an email to addons@tensorflow.org mailing list titled 'Packages up for grabs: …' and listing all packages that they are no longer able to maintain. It is usually a good idea to shortly describe the state of packages, i.e. whether the packages have open bugs, whether they are hard to maintain etc.

* The proxy maintainer must remove themselves from the `CODEOWNERS.md` file, with `<!--maintainer-needed-->` listed in the place of maintainers. This will help other developers to grep packages with no maintainers.

**Notes:**
* [SIG Addons RFC](https://github.com/tensorflow/community/blob/ef626896f30130dfc3b5e75126c94624b689a943/rfcs/20181214-move-to-addons.md).
* [SIG Addons Charter](https://github.com/tensorflow/community/blob/master/sigs/addons/CHARTER.md).

## Questions and Discussion Topics

* What is an optimal time to respond for issues posted to a module?
* How quickly must issues be resolved by proxy maintainers?
* What permissions should proxy maintainers have on the SIG Addons repo?
* What channels of communication should be available for SIG Addons Proxy Maintainers?

## After Request Notes
* Now that the review period has ended, please post all suggested
 additions/removals directly to the tensorflow/addons [issues page](https://github.com/tensorflow/addons/issues)
