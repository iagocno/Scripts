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

-- Criar a GUI
local screenGui = Instance.new("ScreenGui")
screenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

-- Criar os botões para cada checkpoint
for i, checkpoint in ipairs(checkpoints) do
    local button = Instance.new("TextButton")
    button.Size = UDim2.new(0, 200, 0, 50)
    button.Position = UDim2.new(0.5, -100, 0, (i - 1) * 60)
    button.Text = "Checkpoint " .. i
    button.Parent = screenGui
    
    button.MouseButton1Click:Connect(function()
        teleportToCheckpoint(i)
    end)
end
