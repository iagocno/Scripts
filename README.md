local Fluent = loadstring(game:HttpGet("https://github.com/dawid-scripts/Fluent/releases/latest/download/main.lua"))()
local SaveManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/SaveManager.lua"))()
local InterfaceManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/InterfaceManager.lua"))()

local Window = Fluent:CreateWindow({
    Title = "Fluent " .. Fluent.Version,
    SubTitle = "by dawid",
    TabWidth = 160,
    Size = UDim2.fromOffset(580, 460),
    Acrylic = true, -- The blur may be detectable, setting this to false disables blur entirely
    Theme = "Dark",
    MinimizeKey = Enum.KeyCode.LeftControl -- Used when theres no MinimizeKeybind
})

local Tabs = {
    Main = Window:AddTab({ Title = "Main", Icon = "" }),
    Settings = Window:AddTab({ Title = "Settings", Icon = "settings" })
}

local Options = Fluent.Options

-- Referências para os Checkpoints
local checkpoints = {
    game:GetService("Workspace").EventPartFolder["1"].Checkpoint,
    game:GetService("Workspace").EventPartFolder["2"].Checkpoint,
    game:GetService("Workspace").EventPartFolder["3"].Checkpoint,
    game:GetService("Workspace").EventPartFolder["4"].Checkpoint,
    game:GetService("Workspace").EventPartFolder["5"].Checkpoint,
    game:GetService("Workspace").EventPartFolder["6"].Checkpoint,
    game:GetService("Workspace").EventPartFolder["7"].Checkpoint,
    game:GetService("Workspace").EventPartFolder["8"].Checkpoint,
    game:GetService("Workspace").EventPartFolder["9"].Checkpoint,
    game:GetService("Workspace").EventPartFolder["10"].Checkpoint,
    game:GetService("Workspace").EventPartFolder["11"].Checkpoint,
    game:GetService("Workspace").EventPartFolder["12"].Checkpoint,
    game:GetService("Workspace").EventPartFolder["13"].Checkpoint,
    game:GetService("Workspace").EventPartFolder["14"].Checkpoint,
}

-- Função para teletransportar o jogador para um checkpoint específico
local function teleportToCheckpoint(index)
    local checkpoint = checkpoints[index]
    if checkpoint then
        local player = game.Players.LocalPlayer
        local character = player.Character or player.CharacterAdded:Wait()
        character:SetPrimaryPartCFrame(checkpoint.CFrame)
    else
        print("Checkpoint não encontrado!")
    end
end

-- Adicionando o botão de teletransporte na interface
Tabs.Main:AddButton({
    Title = "Teleport to Checkpoint 1", 
    Description = "Click to teleport to checkpoint 1",
    Callback = function()
        teleportToCheckpoint(1)  -- Teleporta para o Checkpoint 1
    end
})

Tabs.Main:AddButton({
    Title = "Teleport to Checkpoint 2", 
    Description = "Click to teleport to checkpoint 2",
    Callback = function()
        teleportToCheckpoint(2)  -- Teleporta para o Checkpoint 2
    end
})

Tabs.Main:AddButton({
    Title = "Teleport to Checkpoint 3", 
    Description = "Click to teleport to checkpoint 3",
    Callback = function()
        teleportToCheckpoint(3)  -- Teleporta para o Checkpoint 3
    end
})

Tabs.Main:AddButton({
    Title = "Teleport to Checkpoint 4", 
    Description = "Click to teleport to checkpoint 4",
    Callback = function()
        teleportToCheckpoint(4)  -- Teleporta para o Checkpoint 4
    end
})

Tabs.Main:AddButton({
    Title = "Teleport to Checkpoint 5", 
    Description = "Click to teleport to checkpoint 5",
    Callback = function()
        teleportToCheckpoint(5)  -- Teleporta para o Checkpoint 5
    end
})

-- Continue adicionando mais botões conforme necessário

Window:SelectTab(1)

Fluent:Notify({
    Title = "Fluent",
    Content = "The script has been loaded.",
    Duration = 8
})

SaveManager:SetLibrary(Fluent)
InterfaceManager:SetLibrary(Fluent)

SaveManager:IgnoreThemeSettings()

SaveManager:SetIgnoreIndexes({})

InterfaceManager:SetFolder("FluentScriptHub")
SaveManager:SetFolder("FluentScriptHub/specific-game")

InterfaceManager:BuildInterfaceSection(Tabs.Settings)
SaveManager:BuildConfigSection(Tabs.Settings)
