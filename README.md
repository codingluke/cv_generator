# CV Generator
Modifying your CV every time you obtain a new diploma or publish a new article can be tedious and time-wasting, even 
when using a document generator such as LaTeX.

CV Generator transforms raw `.json` or `.yml` files into a fully-formatted curriculum vitae in PDF. You won't have to 
deal with graphical/text editors or with LaTeX code anymore, editing that main global file will be enough to obtain your
 updated CV.

## How does it work
The idea behind this project is to separate the content and the template of our _curriculum vitae_. To do so:

* First, you must write your resume following the specified format. You can choose to it using a `.json` file or a 
`.yaml` file. The only requirement is that your document follows the schema provided in the document `cv.schema.json`.
* With your raw resume created, execute the CV Generator as explained in the next sections. A `.tex` file will be 
generated using the template of your choice.
* That `.tex` file is finally compiled into a PDF using LaTeX and saved inside `./generated_documents`.

## How to create your resume
There is only one rule to follow when using CV Generator: follow the syntax provided in `cv.schema.json`. If you are not
 familiar with JSON validation, please read the tutorials provided in [JSON Schema](https://json-schema.org/). Notice 
 that the input file will be validated at the beginning and some errors may arise if the document is not valid.

The easiest and fastest way to start is by departing from the examples provided in `cv.example.en-us.json`,  
`cv.example.es-es.json`, `cv.example.en-us.yaml` and `cv.example.es-es.yaml`.

## How to execute the code
First of all, install the dependencies required by the project. You can do it using `pip` as:

```
pip install -r requirements.txt
```

To execute the code, we must **call the module** directly using the `-m` argument of Python. The following 
snippet summarizes available arguments:

```
Usage:
    python -m cv_generator --cv-file <cv_file_path> --theme <theme_name> [--filename <cv_filename>] [--keep-tex]

Options:
    --cv-file <cv_file_path>    Relative or absolute path to the raw .json or .yaml resume file
    --theme <theme_name>        Name of the theme to use to generate the resume
    --filename <cv_filename>    Name of the theme of the generated resume
    --keep-tex                  Keep LaTeX files used to generate the resume
```

**Note**: to call a module, we must either execute the command from its root directory or have it on the `PYTHONPATH`.

Example:

```
python -m cv_generator --cv-file cv.example.en-us.json --theme sitges --filename example-cv
```

Uses `cv.example.en-us.json` as raw input and formats it using the `sitges` theme. The output file will be stored in 
`./generated_documents/example-cv.pdf`.

## Available themes and examples
Only two themes are available at the moment:

|Theme Name (`<theme_name>`)|Example|Source|
|-|-|-|
|Sitges (`sitges`)|[Example](https://www.dropbox.com/s/ht4cm2fhfegzlnv/cv_generator_samples_sitges.pdf?dl=0)|Self-designed|
|Developer CV (`developer`)|[Example](https://www.dropbox.com/s/32b8act7y95b719/cv_generator_samples_developer.pdf?dl=0)|[LaTeXTemplates.com](https://www.latextemplates.com/template/developer-cv)|

## Contribute
I encourage open-source lovers to implement their designs and to send a pull request so we can all benefit from it. 
Always make sure that the code follows the same structure and that it handles possible missing fields.
