# QB-to-ESX-ESX-to-QB

## Discord
Join our Discord community: [https://discord.com/invite/qApkS3ypxs](https://discord.com/invite/qApkS3ypxs)

---

## QB and ESX Basics

### QB Initialization
```lua
QBCore = nil 

Citizen.CreateThread(function()
	while QBCore == nil do
		TriggerEvent('QBCore:GetObject', function(obj) QBCore = obj end)
		Citizen.Wait(30) -- Wait for 30 seconds
	end
end)
```
For the new version, use the following:
```lua
local QBCore = exports['qb-core']:GetCoreObject()
```

### ESX Initialization
```lua
ESX = nil

Citizen.CreateThread(function()
  while ESX == nil do
    TriggerEvent('esx:getSharedObject', function(obj) ESX = obj end)
    Citizen.Wait(30) -- Wait for 30 seconds
  end
end)
```

---

## Player Events

### Player Loaded Event
This event is triggered when a player connects to the server.
#### QB
```lua
RegisterNetEvent('QBCore:Client:OnPlayerLoaded')
AddEventHandler('QBCore:Client:OnPlayerLoaded',
```
#### ESX
```lua
RegisterNetEvent('esx:playerLoaded')
AddEventHandler('esx:playerLoaded',
```

### Job Update Event
This event is related to the job system.
#### QB
```lua
RegisterNetEvent('QBCore:Client:OnJobUptade')
AddEventHandler('QBCore:Client:OnJobUptade', 
```
#### ESX
```lua
RegisterNetEvent('esx:setJob')
AddEventHandler('esx:setJob',
```

### Player Unload Event
This event is triggered when a player disconnects from the server.
#### QB
```lua
RegisterNetEvent('QBCore:Client:OnPlayerUnload')
AddEventHandler('QBCore:Client:OnPlayerUnload',
```
#### ESX
```lua
RegisterNetEvent('esx:onPlayerDeath')
AddEventHandler('esx:onPlayerDeath',
```

---

## Utility Functions

### Get Closest Player
This function gets the closest player client ID and the distance to the player.
#### QB
```lua
QBCore.Functions.GetClosestPlayer()
```
#### ESX
```lua
ESX.Game.GetClosestPlayer()
```

### Draw 3D Text
This function draws 3D text on the client side.
#### QB
```lua
QBCore.Functions.DrawText3D(1, 1, 1, 'Example')
```
#### ESX
```lua
DrawText3D(1, 1, 1, 'Example') -- (You need to create a function for this.)
ESX.Game.Utils.DrawText3D(1, 1, 1, 'Example') -- ESX already has this function.
```

### Open/Close Menu
Examples of opening and closing menus in ESX and QBCore.
#### QB
```lua
QBCore.UI.Menu.Open
QBCore.UI.Menu.CloseAll() -- (You need to install the default menu script.)
```
#### ESX
```lua
ESX.UI.Menu.Open
ESX.UI.Menu.CloseAll()
```

### Notification Script
Example of a notification script.
#### QB
```lua
TriggerClientEvent("QBCore:Notify", "Text", "success", 2500)

-- server side
QBCore.Functions.Notify("Text", "error")
```
#### ESX
```lua
TriggerEvent('Notification', "Text")

-- client side
ESX.ShowHelpNotification('Text')
```

---

## Inventory Functions

### Get Item by Name
#### QB
```lua
xPlayer.Functions.GetItemByName 
```
#### ESX
```lua
xPlayer.getInventoryItem
```

### Get Player Name
#### QB
```lua
xPlayer.PlayerData.name 
```
#### ESX
```lua
xPlayer.getName()
```

### Job Update
#### QB
```lua
RegisterNetEvent('QBCore:Client:OnJobUpdate')
AddEventHandler('QBCore:Client:OnJobUpdate', function(job)
    PlayerData.job = job
end)
```
#### ESX
```lua
RegisterNetEvent('esx:setJob')
AddEventHandler('esx:setJob', function(job)
    PlayerData.job = job
end)
```

### Add/Remove Money
#### QB
```lua
Player.Functions.AddMoney('bank', amount, "Bank deposit") -- bank
Player.Functions.RemoveMoney('cash', amount, "Bank deposit") -- cash
```
#### ESX
```lua
xPlayer.removeAccountMoney('bank', amount) -- remove money
xPlayer.addMoney(amount) -- add money
```

### Get Bank Money
#### QB
```lua
Player.PlayerData.money["bank"]
```
#### ESX
```lua
xPlayer.getAccount('bank').money
```

### Check Spawn Point
#### QB
```lua
QBCore.Functions.IsSpawnPointClear()
```
#### ESX
```lua
ESX.Game.IsSpawnPointClear()
```

### Set Vehicle Properties
#### QB
```lua
QBCore.Functions.SetVehicleProperties()
```
#### ESX
```lua
ESX.Game.SetVehicleProperties()
```

### Remove Inventory Item
#### QB
```lua
xPlayer.Functions.RemoveItem 
```
#### ESX
```lua
xPlayer.removeInventoryItem 
```

### Add Inventory Item
#### QB
```lua
xPlayer.Functions.AddItem
```
#### ESX
```lua
xPlayer.addInventoryItem
```

### Get Player by ID
#### QB
```lua
QBCore.Functions.GetPlayer(src)
```
#### ESX
```lua
ESX.GetPlayerFromId(src)
```

### Get All Players
#### QB
```lua
QBCore.Functions.GetPlayers(src)
```
#### ESX
```lua
ESX.GetPlayers(src)
```

### Get Player by Citizen ID
#### QB
```lua
QBCore.Functions.GetPlayerByCitizenId(src)
```
#### ESX
```lua
ESX.GetPlayerFromIdentifier(src)
```

### Trim Text
This function trims a text by removing all trailing white spaces.
#### QB
```lua
QBCore.Functions.MathTrim(GetVehicleNumberPlateText(vehicle))
```
#### ESX
```lua
ESX.Math.Trim(value)
```

### Round Number
#### QB
```lua
QBCore.Functions.MathRound(GetVehicleBodyHealth(vehicle), 1),
```
#### ESX
```lua
local value = 5.444

print('value:' .. value) -- returns 5.444
print('rounded value:' .. ESX.Math.Round(value)) -- returns 5
print('rounded value:' .. ESX.Math.Round(value, 1)) -- returns 5.4
```

### Spawn/Delete Vehicle
#### QB
```lua
QBCore.Functions.SpawnVehicle()
QBCore.Functions.DeleteVehicle()
QBCore.Functions.GetVehicleProperties()
QBCore.Functions.GetClosestVehicle()
```
#### ESX
```lua
ESX.Game.SpawnVehicle()
ESX.Game.DeleteVehicle()
ESX.Game.GetVehicleProperties()
ESX.Game.GetClosestVehicle()
```

### Get Player Data
#### QB
```lua
QBCore.Functions.GetPlayerData()
```
#### ESX
```lua
ESX.GetPlayerData()
```

### Create Usable Item
#### QB
```lua
QBCore.Functions.CreateUseableItem()
```
#### ESX
```lua
ESX.RegisterUsableItem()
```

### Remove Money
#### QB
```lua
Player.Functions.RemoveMoney()
```
#### ESX
```lua
xPlayer.removeMoney(money)
```

### Create Callback
#### QB
```lua
QBCore.Functions.CreateCallback()
```
#### ESX
```lua
ESX.RegisterServerCallback()
```

### Trigger Callback
#### QB
```lua
QBCore.Functions.TriggerCallback()
```
#### ESX
```lua
ESX.TriggerServerCallback()
```

### Fetch Status Example
In QBCore, `cid` is used, while in ESX, `identifier` is used. Here is a code block to solve this issue.
#### QB
```lua
QBCore.Functions.CreateCallback('system:fetchStatus', function(source, cb)
    local Player = QBCore.Functions.GetPlayer(source)

     if Player then
           exports['ghmattimysql']:execute('SELECT skills FROM players WHERE citizenid = @citizenid', {
               ['@citizenid'] = Player.PlayerData.citizenid
          }, function(status)
              if status ~= nil then
                   cb(json.decode(status))
              else
                   cb(nil)
              end
          end)
     else
          cb()
     end
end)
```
#### ESX
```lua
ESX.RegisterServerCallback("system:fetchStatus", function(source, cb)
    local src = source
    local user = ESX.GetPlayerFromId(src)


    local fetch = [[
         SELECT
              skills
         FROM
              users
         WHERE
              identifier = @identifier
    ]]

    MySQL.Async.fetchScalar(fetch, {
         ["@identifier"] = user.identifier

    }, function(status)

         if status ~= nil then
              cb(json.decode(status))
         else
              cb(nil)
         end

    end)
end)
```

### Get Items
#### QB
```lua
QBCore.Shared.Items
```
#### ESX
```lua
ESX.GetItems()
```

### Execute SQL
#### QB
```lua
QBCore.Functions.ExecuteSql()
```
#### ESX
```lua
ESX.ExecuteSql() --(ghmattimysql)
MySQL.Async.execute()
```

### Register Command
#### QB
```lua
QBCore.Commands.Add()
```
#### ESX
```lua
RegisterCommand 
```

### Character Data
#### QB
```lua
local Player = QBCore.Functions.GetPlayer(source)
['@citizenid'] = Player.PlayerData.citizenid -- fetch Player
```
#### ESX
```lua
local user = ESX.GetPlayerFromId(src)
["@identifier"] = user.identifier -- fetch user
```

### Math Functions
#### QB
```lua
QBCore.Shared.Trim()
QBCore.Shared.GroupDigits()
```
#### ESX
```lua
ESX.Math.Trim()
ESX.Math.GroupDigits()
```

### Get Closest Object
#### QB
```lua
QBCore.Functions.GetClosestObject()
```
#### ESX
```lua
ESX.Game.GetClosestObject()
```

### Get Vehicle in Direction
#### QB
```lua
QBCore.Functions.GetVehicleInDirection()
```
#### ESX
```lua
ESX.Game.GetVehicleInDirection()
```

### Get Peds
#### QB
```lua
QBCore.Functions.GetPeds()
```
#### ESX
```lua
ESX.Game.GetPeds()
```

### Get Objects
#### QB
```lua
QBCore.Functions.GetObjects()
```
#### ESX
```lua
ESX.Game.GetObjects()
```

### Get Closest Ped
#### QB
```lua
QBCore.Functions.GetClosestPed()
```
#### ESX
```lua
ESX.Game.GetClosestPed()
```

### Spawn Object
#### QB
```lua
QBCore.Functions.SpawnObject()
```
#### ESX
```lua
ESX.Game.SpawnObject()
```
