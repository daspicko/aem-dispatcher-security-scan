[![Test](https://github.com/escalate/aem-dispatcher-security-scan/actions/workflows/test.yml/badge.svg?branch=master&event=push)](https://github.com/escalate/aem-dispatcher-security-scan/actions/workflows/test.yml)

# AEM Dispatcher Security Scan

A commandline tool to perfom an active security scan against a [AEM Dispatcher](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/dispatcher.html).

This tool tries to unify all known security relevant AEM Dispatcher URLs from the internet.

If you know some more URLs, please open a Github issue to report them.

## Usage

### Docker

Start using scanner with minimal effort. Docker images are available in the [GitHub Container Registry](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-container-registry).

Run AEM Dispatcher Scanner as Docker container with default settings

```bash
$ docker run ghcr.io/daspicko/aem-dispatcher-scanner --host http://localhost:8080 
```

Run Docker container with arguments

```bash
$ docker run ghcr.io/aem-dispatcher-scanner \
    --website-url "http://www.adobe.com"
    --page-path "/content/geometrixx/en"
    --timeout 10
```

##### Build local Docker image
If for some reason you want to use local image, build image using
```bash
$ ./aem-dispatcher-scanner.sh
```

### Local development
If you want to customize code or run scanner directly on your machine using Python, setup local environment. Setup use Conda or Virtual environment to install all dependencies.

##### Setup
To start using the tool in terminal, you will need to setup virtual environment and install all dependencies.

```bash
$ ./aem-dispatcher-scanner.sh
```
Run the setup script and choose the setup environment option.

##### Activate virtual environment

If you are using conda
```bash
conda activate "$(pwd)/.venv"
```
othervise if you are using virtualenv then activate environment:
```bash
source .venv/bin/activate
```

##### Dectivate virtual environment
If you are using conda
```bash
conda deactivate
```
othervise if you are using virtualenv then activate environment:
```bash
deactivate
```

##### Starting scanner

Tested with Python 3.12.x on Ubuntu 22.04

If you encounter issues with 3.12.x patch versions of Python, please open a Github issue.

```bash
$ ./scan.py --help

Usage: scan.py [OPTIONS]

    Commandline interface for AEM Dispatcher Security Scan

Options:
    --website-url TEXT        Set URL of website e.g. http://www.adobe.com [required]
    --page-path TEXT  Set path of website page e.g. /content/geometrixx/en
    --timeout FLOAT           Set timeout for http requests in secs e.g. 1.5 or 5
    --help                    Show this message and exit.
```

## Dependencies

* [click](https://pypi.python.org/pypi/click)
* [requests](https://pypi.python.org/pypi/requests)

## References

* [docs.adobe.com](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#testing-dispatcher-security)
* [0ang3el/aem-hacker](https://github.com/0ang3el/aem-hacker)
* [emadshanab/Adobe-Experience-Manager](https://github.com/emadshanab/Adobe-Experience-Manager)
* [danielmiessler/seclists](https://github.com/danielmiessler/SecLists)
* [aem-design/ansible-role-aem-security-test](https://github.com/aem-design/ansible-role-aem-security-test)
* [cognifide/securecq](https://github.com/Cognifide/SecureCQ)
* [perficientdigital.com](https://blogs.perficientdigital.com/2019/01/10/mastering-aem-dispatcher-part-7-securing-the-dispatcher/)
* [infosecinstitute.com](https://resources.infosecinstitute.com/adobe-cq-pentesting-guide-part-1/)

## License

MIT
