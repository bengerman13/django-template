# django-template

This script will create a new Django project using various defaults for US government websites.

## Use for new project

1. Run `pipenv install`
1. Run `pipenv run python 18f_django_template.py`

### Available Options

If any of these options are not provided on the command line, then you will be
prompted for them interactively.

* `--app-name=<new-application-name>`: This is used as the name of the new application's directory and
  a Python identifier is derived from it and used as the name of the new Django
  app inside that directory.

* `--uswds/--no-uswds`: For application's that don't have an HTML frontend, you
can specify `--no-uswds` to not install the US Web Design System (USWDS). If
you do choose to install USWDS, then you will need to have Node.js/npm
installed locally for the installation.

* `--circleci/--no-circleci`: Configure continuous integration with the CircleCI service (or not). The resulting project will have a `.circleci/config.yml` file.

* `--github-actions/--no-github-actions`: Configure continuous integration with Github Actions. The resulting project will have `.github/actions` and `.github/workflows` directories.

### What `18f_django_template.py` does

1. Create a better default `README`
1. Copy `CONTRIBUTING.md` and `LICENSE.md` from the [18F Open Source Policy repo](https://github.com/18F/open-source-policy/)
1. Create a "near-production" `ci` Rails environment, used for running a11y and security scans
1. Create a "near-production" `staging` Rails environment, used for cloud.gov staging environment, with a "TEST SITE" warning banner
1. Create a `.nvmrc` file for specifying the NodeJS version in use
1. Set up `pa11y-ci` for a11y scanning
1. Set up `OWASP ZAP` dynamic security scanning
1. Include `secure_headers` gem and configure CSP header to get OWASP passing by default
1. Install and configure [brakeman](https://rubygems.org/gems/brakeman) for static security scanning
1. Install `bundler-audit` and set up `bundle:audit` rake task for Ruby dependency security scans
1. Set up `yarn:audit` rake task for JavaScript dependency security scans
1. Install [Standard Ruby](https://github.com/testdouble/standard) for Ruby linting
1. Install [rspec](https://rubygems.org/gems/rspec-rails) for unit testing
1. Install [dotenv](https://rubygems.org/gems/dotenv-rails) for local configuration
1. Setup Rails credential diffing
1. Create a separate production credentials file.
1. Create a `pre-commit` hook that can be used to automatically run ruby linter & terraform format
1. Setup USWDS via postcss
1. Setup webpack with `.browserslistrc` from USWDS
1. Update `app/views/layouts/application.html.erb` to pass the `pa11y-ci` scan and include the USWDS Banner
1. Create a `PagesController` and root route
1. Create boundary and logical data model compliance diagrams
1. Create `manifest.yml` and variable files for cloud.gov deployment
1. Optionally run the `rake db:create` and `rake db:migrate` setup steps
1. Optionally create Github Actions workflows for testing and cloud.gov deploy
1. Optionally create terraform modules supporting staging & production cloud.gov spaces
1. Optionally create CircleCI workflows for testing and cloud.gov deploy
1. Optionally create a New Relic config with FEDRAMP-specific host
1. Optionally configure DAP (Digital Analytics Program)
1. Optionally add base translation files and routes for Spanish, French, and Simplified Chinese (es.yml, fr.yml, and zh.yml)
1. Create [Architecture Decision Records](https://adr.github.io/) for above setup
1. Commit the resulting project with git (unless `--skip-git` is passed)

## Development

To run the test suite, run `pipenv install --dev` and then `pipenv run pytest`
from this repository directory.  Make sure you have `npm` and `docker`
installed as some tests require them.

## Contributing

Bug reports and pull requests are welcome on GitHub at
https://github.com/18f/django-template. This project is intended to be a safe,
welcoming space for collaboration, and contributors are expected to adhere to
the [code of
conduct](https://github.com/18f/django-template/blob/main/CODE_OF_CONDUCT.md).

## Code of Conduct

Everyone interacting in the 18F Django Template project's codebases, issue
trackers, chat rooms and mailing lists is expected to follow the [code of
conduct](https://github.com/rahearn/django-template-18f/blob/main/CODE_OF_CONDUCT.md).
