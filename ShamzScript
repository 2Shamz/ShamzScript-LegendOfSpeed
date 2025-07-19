
--[[
    🔥 Shamz Script | Legend Of Speed
    Author: Shamz Studio
    GUI Style: Transparent, Premium Rayfield UI
--]]

local Rayfield = loadstring(game:HttpGet('https://raw.githubusercontent.com/shlexware/Rayfield/main/source'))()

local Window = Rayfield:CreateWindow({
    Name = "Shamz Script | Legend of Speed",
    LoadingTitle = "Shamz Script",
    LoadingSubtitle = "by Shamz Studio",
    ConfigurationSaving = {
        Enabled = true,
        FolderName = "ShamzScriptData",
        FileName = "LegendOfSpeed"
    },
    Discord = {
        Enabled = false,
    },
    KeySystem = false
})

-- Home Tab
local HomeTab = Window:CreateTab("🏠 Home", 4483362458)

HomeTab:CreateSlider({
    Name = "WalkSpeed",
    Range = {16, 500},
    Increment = 5,
    Suffix = "Speed",
    CurrentValue = 16,
    Callback = function(Value)
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = Value
    end,
})

HomeTab:CreateSlider({
    Name = "JumpPower",
    Range = {50, 300},
    Increment = 5,
    Suffix = "Power",
    CurrentValue = 50,
    Callback = function(Value)
        game.Players.LocalPlayer.Character.Humanoid.JumpPower = Value
    end,
})

HomeTab:CreateButton({
    Name = "Enable Infinite Jump",
    Callback = function()
        game:GetService("UserInputService").JumpRequest:Connect(function()
            game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid"):ChangeState("Jumping")
        end)
    end
})

-- Auto Farm Tab
local FarmTab = Window:CreateTab("🌾 Auto Farm", 4483362125)

FarmTab:CreateToggle({
    Name = "Auto Orb",
    CurrentValue = false,
    Callback = function(state)
        _G.AutoOrb = state
        while _G.AutoOrb do wait()
            game.ReplicatedStorage.rEvents.orbEvent:FireServer("collectOrb", "Red Orb", "City")
        end
    end,
})

FarmTab:CreateToggle({
    Name = "Auto Gem",
    CurrentValue = false,
    Callback = function(state)
        _G.AutoGem = state
        while _G.AutoGem do wait()
            game.ReplicatedStorage.rEvents.orbEvent:FireServer("collectOrb", "Gem", "City")
        end
    end,
})

FarmTab:CreateToggle({
    Name = "Auto Hoop",
    CurrentValue = false,
    Callback = function(state)
        _G.AutoHoop = state
        while _G.AutoHoop do wait()
            for _, hoop in pairs(workspace.Hoops:GetChildren()) do
                if hoop:IsA("BasePart") then
                    hoop.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame
                end
            end
        end
    end,
})

FarmTab:CreateToggle({
    Name = "Auto Rebirth",
    CurrentValue = false,
    Callback = function(state)
        _G.AutoRebirth = state
        while _G.AutoRebirth do wait(1)
            game.ReplicatedStorage.rEvents.rebirthEvent:FireServer("rebirthRequest")
        end
    end,
})

-- Teleports Tab
local TeleTab = Window:CreateTab("🌍 Teleports", 4483362723)

local areas = {
    ["Spawn City"] = Vector3.new(-559, 0, 417),
    ["Snow City"] = Vector3.new(-858, 0.5, 2170),
    ["Magma City"] = Vector3.new(1707, 0.5, 4331),
    ["Legends Highway"] = Vector3.new(3594, 215, 7274),
}

for name, pos in pairs(areas) do
    TeleTab:CreateButton({
        Name = name,
        Callback = function()
            game.Players.LocalPlayer.Character:MoveTo(pos)
        end
    })
end

-- Misc Tab
local MiscTab = Window:CreateTab("⚙️ Misc", 4483361860)

MiscTab:CreateKeybind({
    Name = "Toggle GUI",
    CurrentKeybind = "RightControl",
    HoldToInteract = false,
    Callback = function()
        Rayfield:Toggle()
    end,
})

MiscTab:CreateButton({
    Name = "Destroy GUI",
    Callback = function()
        game:GetService("CoreGui").Rayfield:Destroy()
    end
})
