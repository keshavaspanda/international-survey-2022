[![Python 3.9](https://github.com/keshavaspanda/international-survey-2018/actions/workflows/python-package.yml/badge.svg)](https://github.com/softwaresaved/international-survey-2018/actions/workflows/python-package.yml)

# Teaching Research Faculty Survey Analysis

This repository is used to analyse  surveys conducted by the AI for Education Lab.

We ran the **first survey in 2024**, which provided an insight into the demographics, job satisfaction, and practices of Teaching and Research Faculty (TRF) across BITS campuses related to use of AI in Education. To support and broaden this work, the institute will conduct the survey at regular intervals and extend the geographical coverage to facilitate inter-country comparisons. The results of the surveys, anonymised and open licensed, will act as a a valuable resource to understand and improve the working conditions for TRFs using AI.

Our thanks to our partners: Firstname LastName (Location), FirstName LastName and FirstName LastName (Location)....

We have created a survey for all locations (rather than one survey for each one).

This site covers the **2024** survey results.


## Setup

This repository is only for the survey analysis. Here's how to reproduce the analysis on your own computer. The following instructions only apply for the 2024 surveys.

To reproduce the results on your machine, first clone the repository and setup
the Python virtual environment:

```bash
git clone --recurse-submodules https://github.com/keshavaspanda/international-survey-2022
cd international-survey-2022
python -m venv venv  # use python3 if your default python is still Python 2
source venv/bin/activate
python -m pip install -r requirements.txt
```

Use the following to set the environment variables on macOS and Linux. If you are on Windows, use the documentation linked [here](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/set_1).

```bash
export RSE_SURVEY_YEAR=2022  # optional, this is detected automatically if in a folder like *-2018
export RSE_SURVEY_YEAR_PREV=2018  # optional, only needed if previous year != current year - 1
export RSE_SURVEY_FIGURE_TYPE=svg  # optional, set to svg or png to generate figures in that format
export RSE_SURVEY_FIGURE_DPI=300  # optional, set dpi for png or pdf output formats
```

### Generating the full report

You can generate the full report (other than the location specific reports) by running:

```bash
python run.py
```

Location reports should be generated _after_ the section specific reports (do not replace `location` with a specific location, this will generate all country reports):

```bash
python run.py country
```

If you'd like to view this report locally, you can do so via:

```bash
bundle install
bundle exec jekyll serve
```

Then you will be able to view the report by pointing a browser at <http://127.0.0.1:4000/international-survey-2022/>.

### Generating individual sections of the report

To generate sections individually, first ensure that you have run the initialisation (which is the overview and sampling section) that is required by other sections. This can be done by passing `init` to run.py:

```bash
python run.py init
```

This should create a `cache/processed_data.csv` file within the `docs` folder. Once this is generated, you can run any of the sections in any order:

```bash
python run.py <section>
```

### How it works

### Generating the report

So for example to generate the current-employment section: `python run.py current-employment`

* Two types of reports are generated: section reports and country reports. Section reports are useful for comparing countries for a particular section of the survey,
  such as demographics or job satisfaction, whilst country reports give an overview of a country across the different sections of the survey. Both the section and country reports utilise templates from [templates](templates) corresponding to each section (or from [international survey lib submodule repo](https://github.com/softwaresaved/international-survey-lib/tree/main/templates) if they are not found). The country report template `country_report.md` is also found and used from one of these locations in the same way as for sections.
  The template file uses the [Mustache](https://mustache.github.io) templating language via the [chevron](https://pypi.org/project/chevron/) module.
* Section reports are generated in [_section](_section)
* Country reports are generated in [_country](_country)
* Each table in the report has a corresponding CSV in [csv](csv)
* Each figure in the report has a corresponding SVG in [fig](fig)
* The source data used for the analysis is at [data](data)

### Displaying the report as a website

* We use [Jekyll](https://jekyllrb.com) and [Github Pages](https://pages.github.com) to build the website hosted at <https://softwaresaved.github.io/international-survey-2022>.
* Stylesheets for the site are at [_sass](_sass)
* Configuration of the site is at [_config.yml](_config.yml)
* The hosted site can be viewed locally by using the command `bundle exec jekyll serve` in the docs folder and following the localhost URL. If this is the first time setting up Jekyll on your computer, ensure that you have Ruby and Bundle installed (`gem install bundler`).


## Contributors

Here is a list of contributors for the 2024 version of the survey (last name alphabetic order). They are also mentioned in the [.zenodo.json](https://github.com/softwaresaved/international-survey/blob/master/.zenodo.json) to be automatically added to the DOI.

- FirstName LastName, Location
- FirstName LastName, Location
- FirstName LastName, Location
- FirstName LastName, Location
- FirstName LastName, Location
- FirstName LastName, Location
- FirstName LastName, Location
- FirstName LastName, Location
## Licence 

This repository contains code and public data. We have different licence for each
* The code is released under [BSD 3-Clause License](https://github.com/keshavaspanda/international-survey/blob/master/LICENSE.md).
* The data stored in this repository is under the [CC BY 2.5 SCOTLAND](https://github.com/keshavaspanda/international-survey/blob/master/LICENSE_FOR_DATA).

The repository is also archived on Zenodo: <https://doi.org/10.5281/zenodo.xxxxxxx>.
If you want to cite this work and need a citation in a specific format, you can use the citation service on the zenodo.

## Citations

The citation for the 2024 version is:

> - FirstName LastName, FirstName LastName, FirstName LastName, FirstName LastName, FirstName LastName, FirstName LastName, FirstName LastName, FirstName LastName, FirstName LastName. "TRF Survey 2024", Pre-final release for 2024 results (Version 2024-v0.9.0). Zenodo DOI: <https://doi.org/10.5281/zenodo.xxxxxxx>. Check the repository's [citation file](CITATION.cff).


## Funders

The AI for Education Lab is supported by Work Integrated Learning Program, with additional project funding from XXX and XXX. Collaboration between the universities of AAA, BBB, CCC and DDD.
