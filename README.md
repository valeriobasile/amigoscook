amigoscook
==========

Social Cooking Network

API documentation
-----------------

This is the list of possible calls to API functions, with their 
respective arguments and responses. The API always return JSON
structures. An *ID* is an integer numeric value, unique for a
specific type of entity (recipes, users, tools, ingredients, pictures).

**GET requests**

    http://amigoscook.net/recipe/*recipe_id*
---
    http://amigoscook.net/recipes/new?count=*max*
---
    http://amigoscook.net/tool/*tool_id*
---
    http://amigoscook.net/user/*user_id*

**search queries**

    amigoscook.net/recipes/search?q=*search_term*
    amigoscook.net/tools/search?q=*search_term*
    amigoscook.net/ingredients/search?q=*search_term*

return a list of ID:

    {"search":"recipes","query":"lasagna","result":[1234,5678,9012]}

**POST requests**

    http://amigoscook.net/recipe/new

Creates a new recipe. Arguments:

    name (string, required)
    text (string, required)
    ingredients (list of IDs)
    tools (list of IDs)
    user (ID, required)
    
---
    http://amigoscook.net/recipe/edit
    
Modify an existent recipe. 
Arguments:
    id (ID, required)
    name

---
    http://amigoscook.net/recipe/add_picture

Uploads a picture linked to a portion of the recipe text.
If the text span overlaps a previously defined picture link,
the API call returns an error. 
Arguments:

    ID
    picture
    text_from (integer offset)
    text_to (integer offset)

---
    http://amigoscook.net/ingredient/new
    http://amigoscook.net/ingredient/edit

---
    http://amigoscook.net/tool/new
    http://amigoscook.net/tool/edit

