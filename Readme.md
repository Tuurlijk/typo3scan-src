# TYPO3 scanner
Scans code for usage of deprecated and or changed code.

This is the source repository for typo3scan. The actual usable scanner and documentation can be found in the [typo3scan repository](https://github.com/Tuurlijk/typo3scan).

[![demo](https://asciinema.org/a/201851.png)](https://asciinema.org/a/201851?autoplay=1)

TYPO3 publishes [breaking changes and deprecations since version 7](https://docs.typo3.org/typo3cms/extensions/core/stable/Index.html).

This tool scans a folder for any code that is broken or deprecated. It's a wrapper around the [TYPO3 scanner library](https://github.com/ohader/scanner) that has been extracted from the TYPO3 v9 core. You can scan for deprecations and breaking changes for v7, v8, v9 and v10.

## Is TYPO3 scan helping you to migrate your TYPO3 site more smoothly?
Then please consider a sponsorship so I can make this tool even more awesome!
- Become a patron on [Patreon](https://www.patreon.com/michielroos)
- Make a donation via [PayPal](https://paypal.me/MichielRoos)

Thank you! ♥

## Contributing
If you want to help improve this tool to reduce the amount of false positives, improve matchers, add new matchers etc., your contributions are very welcome!

This tool is a wrapper around the [TYPO3 scanner library](https://github.com/ohader/scanner) that has been extracted from the TYPO3 v9 core. I added the v7 and v8 matcher rules to [a fork of this repository](https://github.com/Tuurlijk/scanner).

Most of the time you will want to change the **typo3 scanner library** or your fork of it and then run that library inside the **typo3scan** tool.

### Set up the development environment
Clone the TYPO3 scanner library repository (or your fork of the scanner repository):
```bash
git clone https://github.com/Tuurlijk/scanner.git
```
Clone this repository:
```bash
git clone https://github.com/Tuurlijk/typo3scan.git
```
Add a repository entry to your `composer.json` pointing to your locally cloned *scanner library repository*. Put this one as the first one in the list.
```json
        {
            "type": "path",
            "url": "~/Projects/TYPO3/scanner/"
        },
```
Run `composer update`. Composer will now **link** the local scanner library into the **typo3scan** project. So any changes to the scanner library will be directly reflected when executing typo3scan.

### Run the TYPO3scan tool
You can execute the typo3scan tool from the `bin` directory.
```bash
cd ~/path/to/typo3scan
./bin/typo3scan scan ~/tmp/testExtension
```

### Make sure all the tests run for the scanner library
```bash
cd ~/path/to/scanner-library
composer install
./.Build/bin/phpunit tests/
```

### Build the phar
Make sure you have [Box](https://github.com/box-project/box2) installed.
```bash
box compile
```

## Sponsors
This project was generously sponsored by [Stichting Praktijkleren](https://www.stichtingpraktijkleren.nl/).
