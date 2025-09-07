# Zestro

## Problem:

Every week I go shopping for groceries for the upcoming week. Sometimes the time frame is two weeks and sometimes just for the weekend. Each time, I need to put together a shopping list. This is painful for multiple reasons, takes a lot of time, and I often skip it because I do not want to go through the long and tedius process of building the shopping list. Ultimately, this causes me to spend more than needed, buying too much because I do not know how much is needed. I also tend to forget items that are needed or I do not plan for enough meals to cover the time period, which means I have to make frequent additional trips to the store.

## Solution (MOST IMPORTANT GOAL):
Create a combined shopping list needed to purchase for the meals I plan to cook over a certian period of time.

## Specific Pains when creating a shopping list:
- Finding recipes for the meals I want to shop for and make in the time period I am planning to shop for
- Gathering and writing down all of the ingredients and their quantities for all of the recipes I am shopping for 
- Make a combined (or summed) list of ingredients and quantities. This takes a long time and is error prone (Example: Recipe A calls for 1 lbs of ground beef while recipe B calls for 2 lbs of ground beef for a combined (or summed) total of 3 lbs of ground beef to shop for)
- Making sure all ingredients are counted and summed, double checking all of the recipes in case I have forgotten to add an ingredient (Example: I missed the 1 lbs of ground beef needed for a recipe making my shopping list 1 lbs short requiring an additional trip to the store)
- Often forgetting to buy drinks or snacks or smaller one off purchases (such as frozen meals). Since they are not ingredients for a meal, they get forgotten about and are not added to the list, and as they still need to be shopped for when grocery shopping, often requiring additional shopping trips.
- Some frozen or packaged meals are large enough for multiple servings and can count towards multiple meals, but this is often forgotten about or requires additional planning while at the store shopping
- Having to remember what meals I like, often forget about, or haven't had in a long time (out of sight out of mind)

## Plan (MVP Features):
- Build a website that will allow me to add meals, which consists of one or more recipes and one off items, review previous and saved meal plans, and create new meal plans using my own recipes.
- I want to build recipes with an easy to use, intuitive, and fun interface. (Brain storming required)
- I want to build meals by selecting from recipes I have previously added and have the option to create new recipes if desired.
- I want the ability to select a recipe and scale it for different serving sizes (Example: My meatloaf recipe serves 4 but I am having a dinner party for 8 and want to scale the recipe for this. I typically do this by doubling, trippling, halfing, etc the recipe)
- I should be able to specify the type of meal, recipe, and one off item, such as mexican food or breakfast. Consider using tags or some alternative for specifying meal, recipe and one off item types allowing any number of tags which can be used for searching and filtering. Open to other suggestions and more modern techiniques that will hopefully be explored when brainstorming. (Brain storming required)
- I also want to be able to add one off items to the meals that do not have a recipe, such as chips, snacks, sodas, etc. These one off items are not recipes and should be treated differently but are still added to meals like recipes and should have the same tags or whatever classifying strategy that is used for regular recipes and meals.
- I want each recipe and one off item to typical recipe content such as name, ingredients, directions, serving sizes, prep and cooking time, etc
- I want some sort of representation for each day in the time period I am shopping for that displays the meals for that day. The first thing that comes to mind is a calendar type representation but I do not like this idea, think it is too rigid, and will need help brianstorming alternatives.
- When the day representation is selected, detailed information about the meals and other non meal items (snacks/drinks/etc) would be displayed either to the side of, or in some otherway displayed as a sub section of the day.
- When the detailed information is displayed, I want to be able to easily select and move and/or drag and drop (prefered) meals and one off items onto the detailed information display to add the meal or one off item to the day.
- When I have finished building the meal plan, I want to generate a shopping list containing the combined (summed) ingredient quantities needed to make the meals in the list.
- I want to have some way to print, copy, download or otherwise have the list with me while I am shopping. (Future plans would include a mobile shopping checklist)
- In addition to those possible methods, a way to view the shopping list in a mobile only view is a consideration. Possible implementations could be texting a link to my phone that I can click on and be taken directly to the shopping list, possibly without logging in, making it convenient to quickly view the shopping list on my phone while shopping.
- I want the tone of the text and instructions on the to be light and helpful, almost playful. It should feel like a friendly personal assistant. Friendly sarcasm is a plus.
- I want to have user settings, editable account and profile details. This will allow for individual user preferences.
- I want comprehensive access and feature usage metrics tracking with reporting, allowing me to see what features are most used, what features people spend the most time on, and what features people get hung up on or stop using the site. This information will be useful for forecasting user adoption, additional feature ideas, user workflow enhancement opportunities, etc.
- I want to track what recipes are used together to make up meals (this is primarily for reporting and category based AI model generation)

## Specs:
- This is a full-stack application
- Elm is used for the front end
- F# is used for the back end
- All code, both front end and back end, must strictly adhere to functional programming concepts, designs, and guidelines
- I will need a database but am not sure which to use (I am planning to use the AI brainstorming process to flesh this out)
- I will need a CSS framework with modern, trendy and stylish control designs (I am planning to use the AI brainstorming process to flesh this out)

## UI:
- The UI needs to be brainstormed and prototyped

## Notes:
- The plan and specs inlcuded make up and define the core requirements and experience and must satisfy and address all of the issues, problems and pains mentioned.
- This constitutes the MVP and will be available to all users for free.
- Later phases, features, monitization methods, and other forecasting are to be considered as seperate from the MVP and are not to be considered in the MVP's planning and development

## Revenue/Monitization Plans (Brain Storming Required)
- All features in the current plan will be free to all users
- Subscription based access to certain future features
- Manufacturer deals for coupons or discounts (example: if I am making hamburgers as a meal, discounts for ground beef at store X or manufacturer coupons for brand Y buns offered)
- Deals with stores to highlight special or exlusive deals

## Future Subscription Features (Brain Storming Required)
- Check list of the meals planned that can be checked off as they are made, allowing a quick and easy way to see what remaining meals can be made with the ingredients I have purchased
- Import recipes from image
- Companion mobile application for importing recipes and usage as a shopping checklist
- Cooking techniques and basics tutorial videos (possible collaboration with content provider)
- Shopping list cost based on current store prices (in local area if possible, updated weekly)
- Shopping list broken down by which store has better prices for each item (example: I am willing to go to up to 3 stores, so the list will be separated into three lists based on what I can get at each store the cheapest)
- Recipe hightlights/suggestions based on current store sales and store specials
- Recipe suggestions for meals based on other recipes in the meal and historical recipe usage (using AI model generated from historical recipe usage)

## Future Non-Subscription Ideas:
- Be able to star or favorite meals
- Reminder about meals I have not had after a certain period of time (user setting)
- Recipe sharing/ranking/difficulty
- Pictures of cooked recipe/meal/one off item
