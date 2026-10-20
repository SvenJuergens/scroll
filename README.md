# EXT:scroll

<img src="Resources/Public/Icons/Extension.svg" width="64" alt="EXT:scroll extension icon">

TYPO3 CMS extension to prevent scroll jumps in the backend. It works in the page module as well as in the list view.

> **Fork notice:** This is a maintained fork of [a-r-m-i-n/scroll](https://github.com/a-r-m-i-n/scroll)
> by Armin Vieweg, published as `svenjuergens/scroll`. It adds TYPO3 v14 support and saves the
> scroll position on `pagehide`, because browsers no longer reliably fire `unload`.
> For TYPO3 v12, use the original package `t3/scroll` (2.x).

## Installation

TYPO3 13.4 LTS and 14.3 LTS are supported. The fork is available via Composer only (not in TER):

```
composer require svenjuergens/scroll
```

The package replaces `t3/scroll` and keeps the extension key `scroll`. To switch from the original
package, remove it first:

```
composer remove t3/scroll
composer require svenjuergens/scroll
```

## Setup

There is no configuration. Just install the extension and enjoy the experience :)

## How it works

EXT:scroll registers two JavaScript modules via TYPO3's module loader in the backend. One for the page module ([``ScrollPageModule.js``](./Resources/Public/JavaScript/ScrollPageModule.js))
and another for the list view ([``ScrollRecordList.js``](./Resources/Public/JavaScript/ScrollRecordList.js)).

Both scripts utilize the [sessionStorage API](https://developer.mozilla.org/en-US/docs/Web/API/Window/sessionStorage) 
to store the current scrollTop position when the page is left (`pagehide`).

Next time the page is loaded and a scrollTop value for this page has been stored in sessionStorage, 
the script will scroll to the saved position.

## Support

For help with this fork, please visit the [issue section](https://github.com/SvenJuergens/scroll/issues) on GitHub.

The extension was created by Armin Vieweg. If you like it, you can [donate some funds](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=2DCCULSKFRZFU) to support him. Thank you!

## DDEV Environment

This repository contains a handy DDEV configuration, which allows you to run the extension in a local TYPO3 environment.

More info: https://github.com/a-r-m-i-n/ddev-for-typo3-extensions
