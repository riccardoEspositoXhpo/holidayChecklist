# Holiday Checklist

This repo hosts a google sheets project that attempts to simplify the holiday packing process.

Below are the main features and settings that apply

## Features

- Select the duration of the trip
- Select transport method (car, train or plane)
- Select the temperature at destination (hot, cold, medium)
- Select any specific purpose for this trip (beach, ski, hiking)
- Select if you wish to bring covid-specific items

- Automatically calculate the desired items and their respective quantities to bring on the trip based on the inputs above
- Easy tracking of progress in packing luggage as you "sign-off" items


## How to Use

- Step 1: Navigate to itemInventory tab and basically download your wardrobe in here
  - The more effort goes into this phase, the more effective the sheet will be.
  - Some samples are provided which should help give an idea of the customization context
- Step 2: Select the desired inputs
- Step 3: Run the script(s) from the custom menu
- Step 4: Profit.


## Details (Nerds Only)

This is a simple javascript implementation.
Within Apps Script, we start from vacationOrganizer.gs and work upwards.

- First we clean up any residue of the previous run
- Then we create a few empty objects hosting the categories we require
- We collect the inputs - we're gonne need these to filter out the raw inventory
- We load the item inventory. This is done by loading range --> array of objects --> single nested object
- The inventory is filtered depending on inputs
- itemQuantityGenerator finds items that require a calculation and dynamically constructs a function call, which we store in a string to be evaluated later
- itemOutputGenerator actually "eval"s the functions one by one, takes into consideration any "maxItems" and creates the output object

