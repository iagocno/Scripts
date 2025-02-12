local checkpoints = {
    game:GetService("Workspace").EventPartFolder["14"].Checkpoint,
    game:GetService("Workspace").EventPartFolder["13"].Checkpoint,
    game:GetService("Workspace").EventPartFolder["12"].Checkpoint,
    game:GetService("Workspace").EventPartFolder["11"].Checkpoint,
    game:GetService("Workspace").EventPartFolder["10"].Checkpoint,
    game:GetService("Workspace").EventPartFolder["9"].Checkpoint,
    game:GetService("Workspace").EventPartFolder["8"].Checkpoint,
    game:GetService("Workspace").EventPartFolder["7"].Checkpoint,
    game:GetService("Workspace").EventPartFolder["6"].Checkpoint,
    game:GetService("Workspace").EventPartFolder["5"].Checkpoint,
    game:GetService("Workspace").EventPartFolder["4"].Checkpoint,
    game:GetService("Workspace").EventPartFolder["3"].Checkpoint,
    game:GetService("Workspace").EventPartFolder["2"].Checkpoint,
    game:GetService("Workspace").EventPartFolder["1"].Checkpoint
}

-- Criando a GUI
local ScreenGui = Instance.new("ScreenGui")
local TeleportButton = Instance.new("TextButton")

ScreenGui.Parent = game.CoreGui

TeleportButton.Parent = ScreenGui
TeleportButton.Size = UDim2.new(0, 200, 0, 50)
TeleportButton.Position = UDim2.new(0.5, -100, 0.5, -25)
TeleportButton.Text = "Iniciar Teleporte"
TeleportButton.BackgroundColor3 = Color3.fromRGB(0, 255, 0)
TeleportButton.TextScaled = true

-- Função para teleportar pelos checkpoints
local function teleportPlayer()
    local player = game.Players.LocalPlayer
    if player and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
        for _, checkpoint in ipairs(checkpoints) do
            player.Character.HumanoidRootPart.CFrame = checkpoint.CFrame
            wait(0.5) -- Tempo entre os teleportes (ajustável)
        end
    end
end

-- Conectar a função ao botão
TeleportButton.MouseButton1Click:Connect(teleportPlayer)
