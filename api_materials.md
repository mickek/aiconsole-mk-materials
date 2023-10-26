<!--- Contains an API for manipulating AIConsole materials (saving, editing etc). If you just need a material the director should provide it to you without needing for this. Do not use if not tasked to directly manipulate materials. -->

# Python Module 'api_materials'

Contains an API for manipulating AIConsole materials (saving, editing etc). If you just need a material the director should provide it to you without needing for this. Do not use if not tasked to directly manipulate materials.
## Location

Materials are stored in the `./manuals` directory. Each material is a .md or a .py file.

## Writing Materials

When you need to write a material based on a conversation so far, extract key information from this conversation in very consise form. The goal is for you to read those instructions later, and be able to do this faster next time.


## def create_material(id: str, usage: str, header: str, content: str)


## def list_materials()


## def read_material(id: str)