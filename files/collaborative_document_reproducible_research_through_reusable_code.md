![](https://i.imgur.com/iywjz8s.png)


# Collaborative Document Reproducible Research Through Reusable Code

Welcome to The Workshop Collaborative Document.

This Document is synchronized as you type, so that everyone viewing this page sees the same text. This allows you to collaborate seamlessly on documents.

----------------------------------------------------------------------------

This is the Document for today: https://edu.nl/t7mm4

##  🫱🏽‍🫲🏻 Code of Conduct

Participants are expected to follow these guidelines:
* Use welcoming and inclusive language.
* Be respectful of different viewpoints and experiences.
* Gracefully accept constructive criticism.
* Focus on what is best for the community.
* Show courtesy and respect towards other community members.

For more details, see [here](https://docs.carpentries.org/policies/coc/).

Want to report a Code of Conduct incident and you prefer to do it anonymously? You can do it [here](https://goo.gl/forms/KoUfO53Za3apOuOK2).

## ⚖️ License

All content is publicly available under the Creative Commons Attribution License: [creativecommons.org/licenses/by/4.0/](https://creativecommons.org/licenses/by/4.0/).

## 🙋Getting help

To ask a question, just raise your hand.

If you need help from a helper, place a pink post-it note on your laptop lid. A helper will come to assist you as soon as possible.

## Links

### 🖥 Workshop website
https://esciencecenter-digital-skills.github.io/2026-02-04-ds-reproducible/

## 👩‍🏫👩‍💻🎓 Instructors

Malte Lüken, Ole Mussmann

## 🧑‍🙋 Helpers

Stefan Kirsch

## 🗓️ Agenda
09:45	Introduction
10:00	Software dependencies
10:30	Break
10:45	Software documentation
11:15   Code conventions and modular coding
11:30   Break
11:45   Code conventions and modular coding
12:30	Lunch Break
13:30   Next steps: How to make your code reusable
13:45   Work on project
15:15   Break
15:30	Reusability check
16:15   Wrap up

## :ice_skate: Ice-breaker

"My Most Reproducible Moment": Please share a story about a time your work was successfully reproduced by someone else (or, conversely, a "horror story" where it wasn't).

## 🔧 Exercises

## Time-Capsule of Dependencies

Situation: 5 students (A, B, C, D, E) wrote a code that depends on a couple of libraries. They uploaded their projects to GitHub. We now travel 3 years into the future and find their GitHub repositories and try to re-run their code before adapting it.

### Python (scroll down for R)
    
**A**: You find a couple of library imports across the code but that’s it.

**B**: The README file lists which libraries were used but does not mention any versions.

**C**: You find a `requirements.txt` file with:

```
scipy
numpy
sympy
click
python
git+https://github.com/someuser/someproject.git@master
git+https://github.com/anotheruser/anotherproject.git@master
```

**D**: You find a `requirements.txt` file with:

```
scipy==1.3.1
numpy==1.16.4
sympy==1.4
click==7.0
python==3.8
git+https://github.com/someuser/someproject.git@d7b2c7e
git+https://github.com/anotheruser/anotherproject.git@sometag
```

**E**: You find a `requirements.txt` file with:

```
scipy==1.3.1
numpy==1.16.4
sympy==1.4
click==7.0
python==3.8
someproject==1.2.3
anotherproject==2.3.4
```

### R

**A**: You find a couple of `library()` or `require()` calls across the code but that’s it.

**B**: The `README.md` file lists which libraries were used but does not mention any versions.

**C**: You find a [`DESCRIPTION` file](https://r-pkgs.org/description.html) which contains:

```
Imports:
dplyr,
tidyr
```
    
In addition you find these:

```
remotes::install_github("someuser/someproject@master")
remotes::install_github("anotheruser/anotherproject@master")
```
    
**D**: You find a [`DESCRIPTION` file](https://r-pkgs.org/description.html) which contains:

```
Imports:
dplyr (== 1.0.0),
tidyr (== 1.1.0)
```
    
In addition you find these:

```
remotes::install_github("someuser/someproject@d7b2c7e")
remotes::install_github("anotheruser/anotherproject@sometag")
```
    
**E**: You find a DESCRIPTION file which contains:

```
Imports:
dplyr (== 1.0.0),
tidyr (== 1.1.0),
someproject (== 1.2.3),
anotherproject (== 2.3.4)
```

### Assignment

Answer in the collaborative document:

- Which version do you expect to be easiest to re-run? Why?
- What problems do you anticipate in each solution?

### Answers

#### answers 1
D and E - I would like to test the differences between the released versions of `someproject` and `anotherproject` in E and the specific git hashed/tagged versions in D. There might have been a fix there that was not released.

#### answers 2
D - it shows specific versions for the packages and links to the exact github pages. A problem may be that the code assumes a previous version of the github projects, which I'm not sure if this is included in the link.

#### answers 3
E - it shows the versions of the packages as well as the versions of the previous projects, and hopefully be able to find the previous project sources in previous documentation. But because the previous projects are from other users, not sure if it will be available.

#### answer 4
E - the requirements.txt file gives an overview of the libraries that are used, and which version were installed in the environment. Assuming the code worked three years ago, it should also work when an environment is created with the software packages/libraries installed according to the versions indicated. The same holds for the version of the someproject and anotherproject, which I assume are written by the student(s). 

#### answers 5
D - gives software versions available from packages manager and for specific software github url and version.

#### answers 6
D - the versions are specified and the links can help easily navigate, even for a new user.

#### answers 7
- Solution E will probably be the easiest to reproduce. All requirements are pinned to an exact version. D is very close, with specific git commits pinning a single version.
- Problems with solutions
	- A: There is a risk that dependency versions do not work for the (older) code. Best case, run the code with some installs until it works. Worst case, version hell.
	- B: Same as A, though easier to track down the dependencies. Usually misses some dependencies.
	- C: No versioned dependencies can lead to same problems as A & B. Installing from `master` branch in git is the same as using latest release.
	- D: Installing from git, even though specific commits, does not inspire confidence. Better if the dependency is published on pypi. 
	- All of the `requirements.txt` list `python` as a dependency, which you cannot (to my knowledge) include in this file.

## Writing a Good README

### Assignment

Create a new file called `README.md` in your local project (or improve the `README.md` file for your project).

You can work individually, but you could also discuss whether anything can be improved on your neighbour’s README file(s).

Think about the user (which can be a future you) of your project, what does this user need to know to use or contribute to the project? And how do you make your project attractive to use or contribute to?

(Optional): Try the https://hemingwayapp.com/ to analyse your README file and make your writing bold and clear.

### `README.md` Example
https://github.com/mexca/mexca/blob/main/README.md


## Callenge: Improve Your Code (Format & Lint)

Install and use a formatter and a linter to improve the style of your code.

### Python

[The program `ruff`](https://github.com/astral-sh/ruff) can both format _and_ lint Python code. [Install `ruff`](https://docs.astral.sh/ruff/installation/) from PyPI or conda. Don’t forget to add it to your `requirements.txt`, `pyproject.toml` or whichever file you use to define your dependencies.

#### Formatting

First, use the formatter. Note that the use without the `--check` flag ruff automatically changes your file. This is the default, because formatting does not change the behaviour of your code.

```bash
# Check for formatting
ruff format --check

# Fix formatting, if desired
ruff format
```

Do you agree with the default choices `ruff` made? You can [configure `ruff`](https://docs.astral.sh/ruff/tutorial/#configuration) to follow your choices if you need to, but be aware that the defaults were chosen for a reason.

#### Linting

Next, try out the linter. While fixing formatting is usually harmless, linting fixes change your code on a deeper level. By default, `ruff` only advises you. To automatically apply the linting, you need an explicit `--fix` flag. This is because linting can touch the functionality of your code, so make sure to review the changes ruff makes.

```bash
# Check for linting
ruff check

# Fix linting, if desired
ruff check --fix
```

What is your opinion on the linting suggestions? Again, you can [configure](https://docs.astral.sh/ruff/tutorial/#configuration) the details `ruff` pays attention to when linting. Did you learn something new about the Python language?

## (Optional) Challenge: Git Pre-Commit Hooks
https://carpentries-incubator.github.io/reproducible-research-through-reusable-code-in-1-day/good-code.html#optional-git-pre-commit-hooks

## (Optional) Challenge: Modularity in Python

Carefully review the following code snippet:

```python
def convert_temperature(temperature, unit):
    if unit == "F":
        # Convert Fahrenheit to Celsius
        celsius = (temperature - 32) * (5 / 9)
        if celsius < -273.15:
            # Invalid temperature, below absolute zero
            return "Invalid temperature"
        else:
            # Convert Celsius to Kelvin
            kelvin = celsius + 273.15
            if kelvin < 0:
                # Invalid temperature, below absolute zero
                return "Invalid temperature"
            else:
                fahrenheit = (celsius * (9 / 5)) + 32
                if fahrenheit < -459.67:
                    # Invalid temperature, below absolute zero
                    return "Invalid temperature"
                else:
                    return celsius, kelvin
    elif unit == "C":
        # Convert Celsius to Fahrenheit
        fahrenheit = (temperature * (9 / 5)) + 32
        if fahrenheit < -459.67:
            # Invalid temperature, below absolute zero
            return "Invalid temperature"
        else:
            # Convert Celsius to Kelvin
            kelvin = temperature + 273.15
            if kelvin < 0:
                # Invalid temperature, below absolute zero
                return "Invalid temperature"
            else:
                return fahrenheit, kelvin
    elif unit == "K":
        # Convert Kelvin to Celsius
        celsius = temperature - 273.15
        if celsius < -273.15:
            # Invalid temperature, below absolute zero
            return "Invalid temperature"
        else:
            # Convert Celsius to Fahrenheit
            fahrenheit = (celsius * (9 / 5)) + 32
            if fahrenheit < -459.67:
                # Invalid temperature, below absolute zero
                return "Invalid temperature"
            else:
                return celsius, fahrenheit
    else:
        return "Invalid unit"
```

Refactor the code by extracting functions without altering its functionality.

- What functions did you create?
- What strategies did you use to identify them?

Share your answers in the collaborative document.

#### Solution

https://carpentries-incubator.github.io/reproducible-research-through-reusable-code-in-1-day/good-code.html#optional-modularity-in-python

#### Example project

Example project (if you don't have your own project): https://github.com/popylar-org/prfmodel

### Challenge: Combining Functions

Let’s define two functions that will convert temperature from Fahrenheit to Kelvin, and Kelvin to Celsius:

```R
fahr_to_kelvin <- function(temp) {
  kelvin <- ((temp - 32) * (5 / 9)) + 273.15
  return(kelvin)
}

kelvin_to_celsius <- function(temp) {
  celsius <- temp - 273.15
  return(celsius)
}
```

Define the function to convert directly from Fahrenheit to Celsius, by reusing the two functions above (or using your own functions if you prefer).

## 🧠 Collaborative notes
### Introduction

- Repetition makes reproducibility a routine instead of a complicated thing

#### Version control

- Using git locally is also option
- A messy commit history is better than no commit history

### Software Depedencies

- Cooking analogy:
    - Data -> ingredients
    - Software -> recipes
    - Libraries -> pots, tools

- Libraries (packages that others import): Choose version ranges that are as wide as possible so other packages are compatible with them
- End products (package that has a very specific use case): Pin packages to specific versions; you can update them when needed (e.g., security issue)

Write all packages (with versions) currently installed in your environment to a text file:

```bash
pip freeze > requirements.txt
```

Install all packages from a text file:

```bash
pip install -r requirements.txt
```

### Software Documentation

- `README.md` is the figurehead of your project ✨
    - Title
    - Motivation (what does the project do?)
    - How to set up/install
    - Copy-pastable quick start code example
    - Link or instructions for contributing (see also `CONTRIBUTING.md`)
    - [License](https://choosealicense.com/)
    - Recommended citation (see also `CITATION.cff`)

- If the `README.md` gets too long, consider splitting off a `README.dev.md` for developers' information

> ⚠️ Clear, readable code is better than documenting bad code

### Coding Conventions

- Ruff error codes are linked to entries in ruff documentation that provide more detailed explanations on fixes
- Use `ruff format --diff` to see the suggesting formatting changes

### Modular Code

- Modular code is easier to test:
    - Small components (functions) can be tested with unit tests
- Different stages of the development process require different levels of modularity
    - https://xkcd.com/974/

## Next Steps
- Add a license
    - https://choosealicense.com/
- Go through the FAIR Software Checklist
    - https://fairsoftwarechecklist.net/v0.2/
    - Proudly show off your FAIRness with a badge: https://github.com/fair-software/howfairis
- Add a `CITATION.cff` File
    - https://citation-file-format.github.io/cff-initializer-javascript/
- Publish Your Project on Zenodo
    - https://zenodo.org/login/?next=%2Faccount%2Fsettings%2Fgithub%2F


## 📚 Resources

- Slides: https://nlesc-slides.github.io/2026-02-04_Reproducible_Research/
- Source code slides: https://github.com/NLeSC-slides/2026-02-04_Reproducible_Research
- (online) book **The Turing Way**: A handbook for reproducible, ethical and collaborative research https://book.the-turing-way.org/
- [Choose an Open Source Software license](https://choosealicense.com/) and find out why you [should definitively pick one](https://choosealicense.com/no-permission/)
- [Hemingway App](https://hemingwayapp.com/) to make your writing concise and correct (e.g. for your README)
- A shiny [example project](https://github.com/mexca/mexca) (with maybe a little too many badges)
- Creating issues on GitHub: https://docs.github.com/en/issues/tracking-your-work-with-issues/using-issues/creating-an-issue
- Open Science 101 course by NASA https://stemgateway.nasa.gov/s/course-offering/a0BSJ0000049ih3/open-science-101
- The Dutch Reproducibility Network who organize events and symposia about the topic https://reproducibilitynetwork.nl/
- Subclasses to define custom methods for classes from other libraries. 

    Create your own class that inherits from the library class and add methods.

    ```
    from external_lib import Widget

    class MyWidget(Widget):
        def frobnicate(self, x: int) -> int:
            # use existing Widget API via self
            return self.value + x
    ```

    Use MyWidget instead of Widget wherever you control construction. This is the safest approach.

    Works best when: you can instantiate your subclass (or can wrap factory functions to return it).
    