local CoreGui = game:GetService("StarterGui")CoreGui:SetCore("SendNotification", {    Title = "🗿🍷",    Text = "Loading Content...",    Duration = 5, })print("Loading Content...")		local vu = game:GetService("VirtualUser")		game:GetService("Players").LocalPlayer.Idled:connect(function()		   vu:Button2Down(Vector2.new(0,0),workspace.CurrentCamera.CFrame)		   wait(1)		   vu:Button2Up(Vector2.new(0,0),workspace.CurrentCamera.CFrame)		end)
-- -- TESTES ABAIXO
-- local loopNormal = {
--     while true do
--         for i = 1, 20 do
--             local checkpointName = tostring(i)  -- Converte o número para string
--             local checkpoint = workspace.EventPartFolder:FindFirstChild(checkpointName)
    
--             if checkpoint then
--                 -- Envia os dados para o servidor
--                 game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", checkpoint)
--             end
    
--             task.wait()  -- Espera um pouco antes de continuar
--         end
--     end
-- }

-- local loopInf = {
--     while true do
--         -- Envia dados dos checkpoints de 1 até 20
--         game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["1"])
--         task.wait()
    
--         game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["2"])
--         task.wait()
    
--         game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["3"])
--         task.wait()
    
--         game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["4"])
--         task.wait()
    
--         game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["5"])
--         task.wait()
    
--         game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["6"])
--         task.wait()
    
--         game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["7"])
--         task.wait()
    
--         game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["8"])
--         task.wait()
    
--         game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["9"])
--         task.wait()
    
--         game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["10"])
--         task.wait()
    
--         game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["11"])
--         task.wait()
    
--         game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["12"])
--         task.wait()
    
--         game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["13"])
--         task.wait()
    
--         game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["14"])
--         task.wait()
    
--         game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["15"])
--         task.wait()
    
--         game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["16"])
--         task.wait()
    
--         game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["17"])
--         task.wait()
    
--         game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["18"])
--         task.wait()
    
--         game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["19"])
--         task.wait()
    
--         game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["20"])
--         task.wait()
--     end
-- }
-- -- TESTES ACIMA

local checkpoints = {
    game:GetService("Workspace").EventPartFolder["16"].Checkpoint,
    game:GetService("Workspace").EventPartFolder["15"].Checkpoint,
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
local MainFrame = Instance.new("Frame")
local Title = Instance.new("TextLabel")
local Tabs = Instance.new("Frame")
-- TESTES ABAIXO
local loopNormalButton = Instance.new("TextButton")
local loopInfButton = Instance.new("TextButton")
-- TESTES ACIMA
local CreditsButton = Instance.new("TextButton")
local TeleportButton = Instance.new("TextButton")
local CloseButton = Instance.new("TextButton")
-- TESTES ABAIXO
local loopNormalFrame = Instance.new("Frame")
local loopInfFrame = Instance.new("Frame")
-- TESTES ACIMA
local CreditsFrame = Instance.new("Frame")
local TeleportFrame = Instance.new("Frame")

ScreenGui.Parent = game.CoreGui

MainFrame.Parent = ScreenGui
MainFrame.Size = UDim2.new(0, 250, 0, 300)
MainFrame.Position = UDim2.new(0.5, -125, 0.4, -150)
MainFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
MainFrame.BorderSizePixel = 2
MainFrame.Active = true
MainFrame.Draggable = true

Title.Parent = MainFrame
Title.Size = UDim2.new(1, 0, 0, 30)
Title.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
Title.Text = "Menu"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.TextSize = 18

Tabs.Parent = MainFrame
Tabs.Size = UDim2.new(1, 0, 0, 30)
Tabs.Position = UDim2.new(0, 0, 0, 30)

-- TESTES ABAIXO
loopNormalButton.Parent = Tabs
loopNormalButton.Size = UDim2.new(0.5, 0, 1, 0)
loopNormalButton.Position = UDim2.new(0.5, 0, 0, 0)
loopNormalButton.Text = "Teleportes"
loopNormalButton.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
loopNormalButton.TextColor3 = Color3.fromRGB(255, 255, 255)

loopInfButton.Parent = Tabs
loopInfButton.Size = UDim2.new(0.5, 0, 1, 0)
loopInfButton.Position = UDim2.new(0.5, 0, 0, 0)
loopInfButton.Text = "Teleportes"
loopInfButton.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
loopInfButton.TextColor3 = Color3.fromRGB(255, 255, 255)
-- TESTES ACIMA

CreditsButton.Parent = Tabs
CreditsButton.Size = UDim2.new(0.5, 0, 1, 0)
CreditsButton.Text = "Créditos"
CreditsButton.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
CreditsButton.TextColor3 = Color3.fromRGB(255, 255, 255)

TeleportButton.Parent = Tabs
TeleportButton.Size = UDim2.new(0.5, 0, 1, 0)
TeleportButton.Position = UDim2.new(0.5, 0, 0, 0)
TeleportButton.Text = "Teleportes"
TeleportButton.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
TeleportButton.TextColor3 = Color3.fromRGB(255, 255, 255)

-- TESTES ABAIXO
loopNormalFrame.Parent = MainFrame
loopNormalFrame.Size = UDim2.new(1, 0, 1, -60)
loopNormalFrame.Position = UDim2.new(0, 0, 0, 60)
loopNormalFrame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
loopNormalFrame.Visible = false

loopInfFrame.Parent = MainFrame
loopInfFrame.Size = UDim2.new(1, 0, 1, -60)
loopInfFrame.Position = UDim2.new(0, 0, 0, 60)
loopInfFrame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
loopInfFrame.Visible = false
-- TESTES ACIMA

CreditsFrame.Parent = MainFrame
CreditsFrame.Size = UDim2.new(1, 0, 1, -60)
CreditsFrame.Position = UDim2.new(0, 0, 0, 60)
CreditsFrame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)

TeleportFrame.Parent = MainFrame
TeleportFrame.Size = UDim2.new(1, 0, 1, -60)
TeleportFrame.Position = UDim2.new(0, 0, 0, 60)
TeleportFrame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
TeleportFrame.Visible = false

local CreditText = Instance.new("TextLabel", CreditsFrame)
CreditText.Size = UDim2.new(1, 0, 1, -50)
CreditText.Text = "Criado por iagocno🗿🍷"
CreditText.TextColor3 = Color3.fromRGB(255, 255, 255)
CreditText.BackgroundTransparency = 1
CreditText.TextSize = 16

CloseButton.Parent = CreditsFrame
CloseButton.Size = UDim2.new(1, 0, 0, 30)
CloseButton.Position = UDim2.new(0, 0, 1, -40)
CloseButton.Text = "Fechar UI"
CloseButton.BackgroundColor3 = Color3.fromRGB(200, 0, 0)
CloseButton.TextColor3 = Color3.fromRGB(255, 255, 255)

-- Criando botões de teleporte
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
            -- Envia dados dos checkpoints de 1 até 20
            game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["1"])
            task.wait()
        
            game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["2"])
            task.wait()
        
            game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["3"])
            task.wait()
        
            game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["4"])
            task.wait()
        
            game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["5"])
            task.wait()
        
            game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["6"])
            task.wait()
        
            game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["7"])
            task.wait()
        
            game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["8"])
            task.wait()
        
            game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["9"])
            task.wait()
        
            game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["10"])
            task.wait()
        
            game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["11"])
            task.wait()
        
            game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["12"])
            task.wait()
        
            game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["13"])
            task.wait()
        
            game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["14"])
            task.wait()
        
            game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["15"])
            task.wait()
        
            game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["16"])
            task.wait()
        
            game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["17"])
            task.wait()
        
            game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["18"])
            task.wait()
        
            game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["19"])
            task.wait()
        
            game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder["20"])
            task.wait()
        end
    end)
end)

CloseButton.MouseButton1Click:Connect(function()
    ScreenGui:Destroy()
end)
