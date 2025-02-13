local player = game.Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

-- Criando o ScreenGui e testando
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Parent = playerGui  -- Adiciona a GUI ao PlayerGui

-- Criando o MainFrame
local MainFrame = Instance.new("Frame")
MainFrame.Parent = ScreenGui
MainFrame.Size = UDim2.new(0, 250, 0, 300)
MainFrame.Position = UDim2.new(0.5, -125, 0.4, -150)
MainFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
MainFrame.BorderSizePixel = 2
MainFrame.Active = true
MainFrame.Draggable = true

-- Título do menu
local Title = Instance.new("TextLabel")
Title.Parent = MainFrame
Title.Size = UDim2.new(1, 0, 0, 30)
Title.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
Title.Text = "Menu"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.TextSize = 18

-- Abas do menu
local Tabs = Instance.new("Frame")
Tabs.Parent = MainFrame
Tabs.Size = UDim2.new(1, 0, 0, 30)
Tabs.Position = UDim2.new(0, 0, 0, 30)

-- Botões de navegação (Teleportes, Créditos, Loop Normal, Loop Inf)
local TeleportButton = Instance.new("TextButton")
TeleportButton.Parent = Tabs
TeleportButton.Size = UDim2.new(0.25, 0, 1, 0)
TeleportButton.Text = "Teleportes"
TeleportButton.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
TeleportButton.TextColor3 = Color3.fromRGB(255, 255, 255)

local CreditsButton = Instance.new("TextButton")
CreditsButton.Parent = Tabs
CreditsButton.Size = UDim2.new(0.25, 0, 1, 0)
CreditsButton.Position = UDim2.new(0.25, 0, 0, 0)
CreditsButton.Text = "Créditos"
CreditsButton.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
CreditsButton.TextColor3 = Color3.fromRGB(255, 255, 255)

local loopNormalButton = Instance.new("TextButton")
loopNormalButton.Parent = Tabs
loopNormalButton.Size = UDim2.new(0.25, 0, 1, 0)
loopNormalButton.Position = UDim2.new(0.5, 0, 0, 0)
loopNormalButton.Text = "Loop Normal"
loopNormalButton.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
loopNormalButton.TextColor3 = Color3.fromRGB(255, 255, 255)

local loopInfButton = Instance.new("TextButton")
loopInfButton.Parent = Tabs
loopInfButton.Size = UDim2.new(0.25, 0, 1, 0)
loopInfButton.Position = UDim2.new(0.75, 0, 0, 0)
loopInfButton.Text = "Loop Inf"
loopInfButton.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
loopInfButton.TextColor3 = Color3.fromRGB(255, 255, 255)

-- Frames para cada opção (Teleportes, Créditos, Loop Normal, Loop Inf)
local TeleportFrame = Instance.new("Frame")
TeleportFrame.Parent = MainFrame
TeleportFrame.Size = UDim2.new(1, 0, 1, -60)
TeleportFrame.Position = UDim2.new(0, 0, 0, 60)
TeleportFrame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
TeleportFrame.Visible = false

local CreditsFrame = Instance.new("Frame")
CreditsFrame.Parent = MainFrame
CreditsFrame.Size = UDim2.new(1, 0, 1, -60)
CreditsFrame.Position = UDim2.new(0, 0, 0, 60)
CreditsFrame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)

local loopNormalFrame = Instance.new("Frame")
loopNormalFrame.Parent = MainFrame
loopNormalFrame.Size = UDim2.new(1, 0, 1, -60)
loopNormalFrame.Position = UDim2.new(0, 0, 0, 60)
loopNormalFrame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
loopNormalFrame.Visible = false

local loopInfFrame = Instance.new("Frame")
loopInfFrame.Parent = MainFrame
loopInfFrame.Size = UDim2.new(1, 0, 1, -60)
loopInfFrame.Position = UDim2.new(0, 0, 0, 60)
loopInfFrame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
loopInfFrame.Visible = false

-- Criando o texto de créditos
local CreditText = Instance.new("TextLabel", CreditsFrame)
CreditText.Size = UDim2.new(1, 0, 1, -50)
CreditText.Text = "Criado por iagocno🗿🍷"
CreditText.TextColor3 = Color3.fromRGB(255, 255, 255)
CreditText.BackgroundTransparency = 1
CreditText.TextSize = 16

-- Botão de fechar a interface
local CloseButton = Instance.new("TextButton")
CloseButton.Parent = CreditsFrame
CloseButton.Size = UDim2.new(1, 0, 0, 30)
CloseButton.Position = UDim2.new(0, 0, 1, -40)
CloseButton.Text = "Fechar UI"
CloseButton.BackgroundColor3 = Color3.fromRGB(200, 0, 0)
CloseButton.TextColor3 = Color3.fromRGB(255, 255, 255)

-- Criando a lista de checkpoints
local checkpoints = {}
for i = 1, 20 do
    table.insert(checkpoints, workspace.EventPartFolder[tostring(i)].Checkpoint)
end

-- Criando os botões de teleporte
for i, checkpoint in ipairs(checkpoints) do
    local TeleportOption = Instance.new("TextButton", TeleportFrame)
    TeleportOption.Size = UDim2.new(1, 0, 0, 25)
    TeleportOption.Position = UDim2.new(0, 0, 0, (i - 1) * 30)
    TeleportOption.Text = "Teleportar para " .. i
    TeleportOption.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
    TeleportOption.TextColor3 = Color3.fromRGB(255, 255, 255)

    TeleportOption.MouseButton1Click:Connect(function()
        local player = game.Players.LocalPlayer
        if player and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
            player.Character.HumanoidRootPart.CFrame = checkpoint.CFrame
        end
    end)
end

-- Funções para alternar entre abas
CreditsButton.MouseButton1Click:Connect(function()
    CreditsFrame.Visible = true
    TeleportFrame.Visible = false
    loopNormalFrame.Visible = false
    loopInfFrame.Visible = false
end)

TeleportButton.MouseButton1Click:Connect(function()
    CreditsFrame.Visible = false
    TeleportFrame.Visible = true
    loopNormalFrame.Visible = false
    loopInfFrame.Visible = false
end)

loopNormalButton.MouseButton1Click:Connect(function()
    CreditsFrame.Visible = false
    TeleportFrame.Visible = false
    loopNormalFrame.Visible = true
    loopInfFrame.Visible = false
    -- Iniciando o Loop Normal (ajuste conforme a lógica)
    spawn(function()
        while true do
            for i = 1, 20 do
                local checkpointName = tostring(i)  -- Converte o número para string
                local checkpoint = workspace.EventPartFolder:FindFirstChild(checkpointName)

                if checkpoint then
                    -- Envia os dados para o servidor
                    game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", checkpoint)
                end

                task.wait()  -- Espera um pouco antes de continuar
            end
        end
    end)
end)

loopInfButton.MouseButton1Click:Connect(function()
    CreditsFrame.Visible = false
    TeleportFrame.Visible = false
    loopNormalFrame.Visible = false
    loopInfFrame.Visible = true
    -- Iniciando o Loop Inf (ajuste conforme a lógica)
    spawn(function()
        while true do
            for i = 1, 20 do
                game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder[tostring(i)])
                task.wait()
            end
        end
    end)
end)

CloseButton.MouseButton1Click:Connect(function()
    ScreenGui:Destroy()
end)

-- Exibindo notificação inicial
local CoreGui = game:GetService("StarterGui")
CoreGui:SetCore("SendNotification", {
    Title = "🗿🍷",
    Text = "Loading Content...",
    Duration = 5,
})
print("Loading Content...")
