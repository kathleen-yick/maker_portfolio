HOW THIS FOLDER IS ORGANISED
============================
Everything you give the website lives in here. Each folder has a
notes.txt that tells you exactly what to put in it.

images/
  README.txt                 this file

  about/                     the About Me tab
    notes.txt                introduction + Additional Info rows
    portrait.jpg             tall photo beside the introduction
    side.jpg                 square photo beside Additional Info

  resume/                    the Resume tab
    notes.txt
    resume.pdf               your resume; the page shows it with download button

  life/                      the Life tab
    notes.txt                two paragraphs + Elsewhere links
    1.jpg  2.jpg  ...        photos, numbered in display order (up to 6)

  example-project/           the Projects tab: copy this folder per project
    notes.txt                title, year, blurb, description...
    1.png  2.png  3.png      files, numbered in display order (1 = thumbnail)
    4.pdf                    .jpg / .jpeg / .png / .pdf, 1 to 6 per project

  rapid-data-collection-box/ your first project folder (same layout)

Then, in a Claude Code session in this folder, say something like:
  "add the new projects in images/"
  "update the About Me page from images/about"
  "add the resume"
  "update the Life page from images/life"
and the text and file paths are written into index.html for you to refine.
