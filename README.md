--[[
====================================================================================
                            HOW TO USE BLINDHUBSUILIBRARY
====================================================================================

This guide explains how to use the core functions of the library.

------------------------------------------------------------------------------------
1. Window
------------------------------------------------------------------------------------

-- How do you create the main window?
-- The first step is to create the main UI window. You can give it a custom title.

local Library = require(script.Parent.BlindHubsUiLibrary) -- Make sure to require the library
local Window = Library.CreateWindow({
    Title = "My Awesome Hub"
})

------------------------------------------------------------------------------------
2. Tabs
------------------------------------------------------------------------------------

-- How do you add a new tab to the window?
-- All UI elements must be placed inside a tab.

local mainTab = Window:AddTab("Main")
local settingsTab = Window:AddTab("Settings")

------------------------------------------------------------------------------------
3. UI Elements
------------------------------------------------------------------------------------

-- How do you add elements?
-- You call the element functions on the tab object you want to add them to (e.g., mainTab).

-- BUTTON
-- Example:
local myButton = mainTab:AddButton("Click Me!")

-- BUTTON (with options)
local myIconButton = mainTab:AddButton({Text = "Kill Aura", Icon = true})

-- LABEL
-- Example:
mainTab:AddLabel("Player Options")

-- TOGGLE
-- Example:
local espToggle = mainTab:AddToggle("Player ESP")

-- SLIDER
-- Example:
local speedSlider = mainTab:AddSlider({
    Text = "Walkspeed",
    Min = 16,
    Max = 200,
    Default = 50
})

-- DROPDOWN
-- Example:
local targetDropdown = mainTab:AddDropdown({
    Text = "Target Priority",
    Options = {"Closest", "Richest", "Random"}
})

------------------------------------------------------------------------------------
4. Handling User Input
------------------------------------------------------------------------------------

-- How do you make the elements do things?
-- For buttons, you connect to the 'MouseButton1Click' event.
-- For toggles, sliders, and dropdowns, you connect to the '.State.Changed' event.

-- Button Click Example:
myButton.MouseButton1Click:Connect(function()
    print("Button was clicked!")
end)

-- Toggle State Change Example:
espToggle.State.Changed:Connect(function(isEnabled)
    if isEnabled then
        print("ESP has been turned ON.")
    else
        print("ESP has been turned OFF.")
    end
end)

-- Slider Value Change Example:
speedSlider.State.Changed:Connect(function(newValue)
    print("Walkspeed set to: " .. newValue)
    game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = newValue
end)

-- Dropdown Selection Change Example:
targetDropdown.State.Changed:Connect(function(selectedOption)
    print("Target priority changed to: " .. selectedOption)
end)

------------------------------------------------------------------------------------
5. Advanced Window Customization
------------------------------------------------------------------------------------

-- How do you change the UI theme color?
-- Available themes: "Purple", "Pink", "Red", "Blue", "Green", "Orange", "Black"

Window:SetTheme("Red")

-- How do you change the UI transparency?
-- Use a value from 0 (fully transparent) to 100 (fully opaque).

Window:SetTransparency(80) -- Sets the UI to be mostly opaque

]]
