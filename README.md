amigoscook
==========

Amigoscook is an online Social Cooking Network, where the emphasis is on
"Social Cooking", which means prepare food together.

* **OK, it's your usual recipes database**
Not true! in Amigoscook you can upload your own recipes, and create remixes 
of other peoples recipes. Your version of lasagna is better than that of 
@awesomecook? Remix it!


API documentation
-----------------

This is the list of possible calls to API functions, with their 
respective arguments and responses. The API always return JSON. 
An *ID* is an integer numeric value, unique for a
specific type of entity (recipes, users, tools, ingredients, pictures).

**GET requests**

Get a recipe by id

    http://amigoscook.com/recipe/*recipe_id*
    return example:
    {"id":1234,"name":"lasagna","ingredients":[{"id":5678,"name":
    "tomato sauce","description":"sauce made from tomato"},
    {"id":3456,"name":"minced meat","description":
    "meat that has been minced"}],
    "tools":[{"id":9012,"name":"spoon","description":
    "excavates the food"},{"id":7890,"name":"knife","description":
    "cuts the food"}]}

Get new recipes

    http://amigoscook.com/recipes/new?count=*max*
    
Returns up to *count* recipes, starting from the ones with the most recent upload timestamp.

Get a tool by id

    http://amigoscook.com/tool/*tool_id*

Get an ingredient by id

    http://amigoscook.com/tool/*tool_id*

Get a user profile

    http://amigoscook.com/user/*user_id*

---

**search queries**

    http://amigoscook.com/search
GET arguments:

* **type**: "recipe", "tool", "ingredient".
* **q**: Search term. The search will return recipes that contains the search term(s) in the name or in the description.
* **tool**: id or name of a tool, When searching for recipes, it returns only recipes that use the specified tool.
* **ingredient**: id or name of an ingredient. When searching for recipes, it returns only recipes that use the specified ingredient. 

The search API returns a list of recipes.

---

**POST requests**

    http://amigoscook.com/recipe/new

* Creates a new recipe. Arguments:

    name (string, required)
    text (string, required)
    user (ID, required)
    
* Edit a recipe

    http://amigoscook.com/recipe/*recipe_id*/edit
    
* Modify an existent recipe. 
Arguments:
    name (string)
    
* Add picture to text

    http://amigoscook.com/recipe/*recipe_id*/add_picture

Uploads a picture linked to a portion of the recipe text.
If the text span overlaps a previously defined picture link,
the API call returns an error. 
Arguments:

    picture
    text_from (integer offset)
    text_to (integer offset)

* Add/edit ingredients

    http://amigoscook.net/ingredient/*ingredient_id*/new
    http://amigoscook.net/ingredient/*ingredient_id*/edit

* Add/edit tools

    http://amigoscook.net/tool/*tool_id*/new
    http://amigoscook.net/tool/*tool_id*/edit

