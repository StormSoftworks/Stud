# Stud
An roblox ui library
https://discord.gg/tmmWWKT8YA

# Documents

**Initialization**
```lua
local field = loadstring(game:HttpGet("https://raw.githubusercontent.com/StormSoftworks/Stud/refs/heads/main/loadstring"))()
```

**Creating a window**
```lua
local window = field:NewWindow({
	WindowName = "Test"; -- sets the window's name
	WindowImage = "rbxassetid://14187686429"; -- sets the window's icon
	Configuration = {
		Shadow = false;
		WindowSize = nil; -- if nil will use default size / scaled size for device.	
	},
	OpenButton = {
		Image = ""; -- self explanatory
		Size = nil; -- sets the openbutton's size, if nil will use default size / scaled size for device.
		Draggable = true; 
	},
	Premium = {
		Local = {
			GamepassID = 1234567890
		}
	}
})
```

**Icons**
```lua
local geticons = field:GetIconsTable() -- returns icons table.
```

**Custom Premium Function**
```lua
local ispremium = window:PremiumState()
```

**Creating a tab**
```lua
local tab1 = window:CreateTab({
	TabName = "Test";
	TabImage = "rbxassetid://11432862087";
})
```

**Creating a section**
```lua
local section1 = tab1:CreateSection({
	SectionTitle = "Section Test";
	SectionDescription = "heya!";
	SectionImage = "rbxassetid://11432862087";
})
```

**Creating a button**
```lua
local button = section1:CreateButton({
	ButtonName = "button test";
	Callback = function()
		print("hewo :#")
	end,
})
```

**Creating a checkbox**
```lua
local checkbox = section1:CreateCheckbox({
	CheckboxName = "Box :#";
	Callback = function(retval)
		print("checkbox value: " .. tostring(retval))
	end,
})
```

**Creating a -KEYBIND- checkbox (PC ONLY)**
```lua
local kbcheckbox = section2:CreateKBCheckBox({
	CheckboxName = "Keybind",
	Callback = function(retvalue)
		print(tostring(retvalue) .. " - keybind checkbox")
	end,
})
```

**Creating a textbox**
```lua
local textbox = section1:CreateTextBox({
	TextboxName = "Test";
	PlaceHolder = ""; -- Leave empty if you don't have any, will replace with "Enter any string here."
	Text = ""; -- Leave empty if you don't have any.
	Callback = function(str)
		print("heya! txt box said: " .. str)
	end,
})
```

**Creating a notification**
```lua
window:Notify({
	Title = "test";
	Description = "idk";
	Duration = 5;
})
```

**Creating labels and messages**
```lua
local label = section1:CreateLabel({ Text = "Hewo!" })
local warning = section1:CreateWarning({ Text = "Hewwo!" })
local error = section1:CreateError({ Text = "Hewwwo!" })
local success = section1:CreateSuccess({ Text = "Hewwwwo-!" })
```

**Creating a slider**
```lua
local slider = section1:CreateSlider({
	SliderName = "WalkSpeed";
	Min = 0;
	Max = 100;
	Default = 16;
	Callback = function(v)
		print(v)
		-- game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = v
	end,
})
```

**Creating another section**
```lua
local section2 = tab1:CreateSection({
	SectionTitle = "Dropdown Test";
	SectionDescription = "wazzup";
	SectionImage = "rbxassetid://11432862087";
})
```

**Creating a dropdown**
```lua
local dropdown1 = section2:CreateDropdown({
	DropdownName = "Tezttttt";
	Default = "helo :3";
	Entries = {"helo :#", "helo :$"};
	Callback = function(v)
		print(v)
	end,
})
```

# Settings
```lua
--- Settings
-- ====================================================================================================================================================
local CustomizableImage = Instance.new("ImageLabel", game:GetService("Players").LocalPlayer.PlayerGui:WaitForChild('StudLibrary'):WaitForChild('Main'))
CustomizableImage.Size = UDim2.new(1,0,1,0)
CustomizableImage.ZIndex = 1
CustomizableImage.BackgroundTransparency = 1
CustomizableImage.ImageTransparency = .94
CustomizableImage.Image = ""

local SettingsPage = {}

SettingsPage.SettingTab = window:CreateTab({
	TabName = "Settings";
	TabImage = "rbxassetid://11293977610";
})

SettingsPage.SettingSection = SettingsPage.SettingTab:CreateSection({
	SectionTitle = "UI";
	SectionDescription = "Offer's an costumizable settings page UI for Stud ui library";
	SectionImage = "rbxassetid://14187686429";
})

SettingsPage.ThemeSection = SettingsPage.SettingTab:CreateSection({
	SectionTitle = "Themes";
	SectionDescription = "Display's all the theme's you can use for this library.";
	SectionImage = "rbxassetid://12967676465";
})

SettingsPage.SettingSection:CreateTextBox({
	TextboxName = "Background Image";
	PlaceHolder = "rbxassetid://11293977610"; -- Leave empty if you don't have any, will replace with "Enter any string here."
	Text = ""; -- Leave empty if you don't have any.
	Callback = function(str)
		CustomizableImage.Image = str
	end,
})

SettingsPage.SettingSection:CreateTextBox({
	TextboxName = "BackgroundColor3",
	PlaceHolder = "255,255,255 / Default", -- Leave empty if you don't have any, will replace with "Enter any string here."
	Text = "", -- Leave empty if you don't have any.
	Callback = function(str)
		-- Split the string by commas and convert to numbers
		local r, g, b = str:match("(%d+),(%d+),(%d+)")
		if r and g and b then
			r, g, b = tonumber(r), tonumber(g), tonumber(b)
			-- Clamp between 0 and 255, then convert to 0–1 range
			r, g, b = math.clamp(r, 0, 255) / 255, math.clamp(g, 0, 255) / 255, math.clamp(b, 0, 255) / 255
			local color = Color3.new(r, g, b)

			-- Apply the color
			local playerGui = game:GetService("Players").LocalPlayer:WaitForChild("PlayerGui")
			local mainGui = playerGui:WaitForChild("StudLibrary"):WaitForChild("Main")

			mainGui.GroupColor3 = color
		else
			warn("Invalid color format. Use: R,G,B (e.g., 255,255,255)")
		end

		if str == "Default" then
			local playerGui = game:GetService("Players").LocalPlayer:WaitForChild("PlayerGui")
			local mainGui = playerGui:WaitForChild("StudLibrary"):WaitForChild("Main")

			mainGui.GroupColor3 = Color3.fromRGB(255,255,255)
		end
	end,
})

SettingsPage.SettingSection:CreateButton({
	ButtonName = "Reset UI Size";
	Callback = function()
		window["2"].Size = UDim2.new(0.392, 0,0.47, 0)
	end,
})

--[[
SettingsPage.SettingSection:CreateTextBox({
	TextboxName = "Title Renaming",
	PlaceHolder = "Stud -- string",
	Text = "",
	Callback = function(str)
		local playerGui = game:GetService("Players").LocalPlayer:WaitForChild("PlayerGui")
		local mainGui = playerGui:WaitForChild("StudLibrary"):WaitForChild("Main")
		mainGui.Topbar.TextLabel.Text = str
	end,
})
--]]

SettingsPage.SettingSection:CreateDropdown({
	DropdownName = "Theme",
	Default = "Default",
	Entries = {"Amethyst","Dark","Default", "Crimson"},
	Callback = function(v)
		local playerGui = game:GetService("Players").LocalPlayer:WaitForChild("PlayerGui")
		local mainGui = playerGui:WaitForChild("StudLibrary"):WaitForChild("Main")

		if v == "Amethyst" then
			mainGui.GroupColor3 = Color3.fromRGB(185, 167, 255)
		elseif v == "Dark" then
			mainGui.GroupColor3 = Color3.fromRGB(127, 127, 127)
		elseif v == "Default" then
			mainGui.GroupColor3 = Color3.fromRGB(255,255,255)
		elseif v == "Crimson" then
			mainGui.GroupColor3 = Color3.fromRGB(255, 149, 149)
		end
	end
})

SettingsPage.ThemeSection:CreateCheckbox({
	CheckboxName = "Shadow";
	Callback = function(retval)
		window:Shadow(retval)
	end,
})
```
