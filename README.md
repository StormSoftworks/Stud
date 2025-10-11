# Stud
An roblox ui library

# Documents

**Initialization**
```lua
local field = loadstring(game:HttpGet("https://raw.githubusercontent.com/StormSoftworks/Stud/refs/heads/main/loadstring"))()
```

**Creating a window**
```lua
local window = field:NewWindow({
	WindowName = "Test";
	WindowImage = "rbxassetid://14187686429";
})
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
