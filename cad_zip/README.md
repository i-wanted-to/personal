# cad_zip

Compress and uncompress FreeCAD projects.

FreeCAD saves a project as a ZIP archive containing many text documents. Tiny changes in text
content result in massive changes in the saved ZIP file, leading to very inefficient storage in
difference-based version control.

This tool automates the process of unzipping the project (so the text contents can be efficiently
stored in version control), and re-zipping the project (so it can be opened by FreeCAD). Extra care
must be taken, as FreeCAD depends not only on the compressed contents, but also on the particular
structure of the ZIP file itself.
