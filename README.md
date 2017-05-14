# pandoc-templates

Draft but usable templates for [pandoc](http://pandoc.org/) with proper support for Greek text.


## to-do

- [ ] strip down to essential packages
- [ ] create image & PDF previews


## build system

The following is a complementary example for a [Sublime Text](https://www.sublimetext.com/) build system. You cannot copy/paste it and expect it to work.

```
{
    "selector": "text.html.markdown",
    "shell": true,
    "cmd": [
        "pandoc",
        "--latex-engine", "%programfiles%/MiKTeX 2.9/miktex/bin/x64/xelatex.exe",

        "-f", "markdown+yaml_metadata_block+citations+pandoc_title_block+implicit_figures+link_attributes", // markdown_mmd ignoes latex commands
        
        "-V", "fontsize=12pt",
        // "-V", "mainfont=Ubuntu",
        // "-V", "classoption:openright",

        //%appdata%\Pandoc\templates
        // "--template", "handout.tex",
        "--template", "typical.tex",

        // "--toc", // table of contents
        // "-S", // produce typographically correct output, automatic?

        // "--biblatex",
        "--bibliography", "C:/archives/texts/citations.bib",
        "--csl", "C:/archives/texts/greek-chicago-x.csl",
        // "--csl", "C:/archives/texts/chicago-fullnote-bibliography-no-ibid.csl",

        "-o", "$file_base_name.pdf", "$file_name",
        "&", //*nix users should replace the & with a ;
        "C:/portable/SumatraPDF/SumatraPDF.exe", "$file_base_name.pdf", // preview PDF
    ]
}
```
