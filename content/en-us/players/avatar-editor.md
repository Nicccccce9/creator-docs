---
title: Avatar Editor Service
description: The Avatar Editor Service allows access to a user's avatar and inventory and Marketplace.
---

The Avatar Editor Service lets you access and make changes to a user's avatar within an expm/catalog) to save outfits and purchase avatar items to the user's account.

We recommend implementing the Avatar Editor Service with an in-game avatar editor for a complete character customization experience. See the [Simple Avatar Editor Demo](https://www.roblox.com/games/9376329300/Simple-Avatar-Editor-Demo) reference place for an example of this feature.

To begin using the Avatar Editor Service, you must first [request access](#request-access)uccessfully granted, you can perform the following actions:

- [Read user's inventory](#read-user-inventory) to get a list of items owned by the user.
- [Search the Marketplace](#search-the-marketplace), using a variety of properties to filter and sort.
- [Equip avatar items and save outfits
- [Prompt the user to purchase](#purchase-items) an Marketplace item.

## Request access

To begin accessing a user's inventory, you need to prompt the user to allow access through `Class.AvatarEditorService:PromptAllowInventoryReadAccess()|PromptAllowInventoryReadAccess()`. You need to perform this request once per session.

Use the following code sample to initiate the access prompt and listen for the user response:

```lua
local AvatarEditorService = game:GetService("AvatarEditorService")

AvatarEditorService:PromptAllowInventoryReadAccess()

local result = AvatarEditorService.PromptAllowInventoryReadAccessCompleted:Wait()

if result == Enum.AvatarPromptResult.Success then
  -- Access granted!
end
```

The user receives the following prompt:

<img src="../assets/avatar/avatar-editor-service/Avatar-Editor-Access-Items.png" width="400" />

Once the user accepts the prompt, the `Class.AvatarEditorService` can begin accessing the user's inventory.

## Read user inventory

Once access is granted by the user, you can read their inventory with the `Class.AvatarEditorService:GetInventory()|GetInventory()` function, supplying an array of `Enum.AvatarAssetType|AvatarAssetTypes` to filter by. This function returns an `Class.InventoryPages` object containing the user owned items.

Use the following code sample to print a list of specific accessories in a user's inventory:

```lua
local AvatarEditorService = game:GetService("AvatarEditorService")

AvatarEditorService:PromptAllowInventoryReadAccess()

local result = AvatarEditorService.PromptAllowInventoryReadAccessCompleted:Wait()

if result == Enum.AvatarPromptResult.Success then
  -- Access granted!
  local assetType
## Search the Marketplace

`Class.AvatarEditorService` includes functions and events which let you search the Roblox catalog. To search, supply your query with a `Datatype.CatalogSearchParams` object that includes one or more of the following properties:

<table>
<thead>

  </tr>
</thead>
<tbody>
    <td>AssetTypes</td>
    <td>An array of `Enum.AvatarAssetType` such as Enum.AvatarAssetType.BackAccessory.</td>
  </tr>
  <tr>
    <td>BundleTypes</td>
    <td>An array of `Enum.BundleType` such as Enum.BundleType.BodyParts.</td>
  </tr>
  <tr>
    <td>CategoryFilter</td>
    <td>A `Enum.CatalogCategoryFilter` describing the various catalog categories like "Featured" or "Community Creations". By default this is set to `Enum.CatalogCategoryFilter.None`</td>
  </tr>
  <tr>
    <td>MaxPrice</td>
    <td>An integer describing the maximum price to filter.</td>
  </tr>
  <tr>
    <td>MinPrice</td>
    <td>An integer describing the minimum price to filter. By default, MinPrice is <b>0</b>.</td>
  </tr>
  <tr>
    <td>SearchKeyword</td>
    <td>A string to query against item descriptions in the catalog.</td>
  </tr>
  <tr>
    <td>SortType</td>
    <td>An integer to specify a given creator. You can use either a UserId or a GroupId.</td>
  </tr>
  <tr>
  <td>CreatorName</td>
    <td>A string used to search by items created by a given creator. You can use either a User Name or a Group Name.</td>
  </tr>
</tce")

local catalogSearchParams = CatalogSearchParams.new()
local assetTypes = {

  Enum.AvatarAssetType.ShoulderAccessory
}
catalogSearchParams.AssetTypes = assetTypes

local pagesObject =
--This function returns a CatalogPages object containing the results.
AvatarEditorService:SearchCatalog(catalogSearchParams)
local currentPage = pagesObject:GetCurrentPage()
for _, item in currentPage do
  print(item)
end
``Class.AvatarEditorService:PromptSaveAvatar()|PromptSaveAvatar()`. This may include:

- Pre-defined ava
local Players = game:GetService("Players")

local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")

local currentDescripti
The following code sample creates an outfit with `Class.AvatarEditorService:PromptCreateOutfit()` and listens for a successful `Class.AvatarEditorService.PromptCreateOutfitCompleted` event:

</Alert>
