local CoreGui = game:GetService("StarterGui")
CoreGui:SetCore("SendNotification", {
    Title = "🗿🍷",
    Text = "Loading Content...",
    Duration = 5,
})

print("Loading Content...")

local vu = game:GetService("VirtualUser")
game:GetService("Players").LocalPlayer.Idled:connect(function()
    vu:Button2Down(Vector2.new(0,0),workspace.CurrentCamera.CFrame)
    wait(1)
    vu:Button2Up(Vector2.new(0,0),workspace.CurrentCamera.CFrame)
end)

local checkpoints = {}
for i = 1, 20 do
    local checkpoint = game:GetService("Workspace").EventPartFolder[tostring(i)] and game:GetService("Workspace").EventPartFolder[tostring(i)].Checkpoint
    if checkpoint then
        table.insert(checkpoints, checkpoint)
    end
end

-- Criando a GUI
local ScreenGui = Instance.new("ScreenGui")
local MainFrame = Instance.new("Frame")
local Title = Instance.new("TextLabel")
local Tabs = Instance.new("Frame")
local CreditsButton = Instance.new("TextButton")
local TeleportButton = Instance.new("TextButton")
local CloseButton = Instance.new("TextButton")
local CreditsFrame = Instance.new("Frame")
local TeleportFrame = Instance.new("Frame")
local LoopButton = Instance.new("TextButton")
local LoopInfButton = Instance.new("TextButton")

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

CreditsFrame.Parent = MainFrame
CreditsFrame.Size = UDim2.new(1, 0, 1, -60)
CreditsFrame.Position = UDim2.new(0, 0, 0, 60)
CreditsFrame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)

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

TeleportFrame.Parent = MainFrame
TeleportFrame.Size = UDim2.new(1, 0, 1, -60)
TeleportFrame.Position = UDim2.new(0, 0, 0, 60)
TeleportFrame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
TeleportFrame.Visible = false

LoopButton.Parent = TeleportFrame
LoopButton.Size = UDim2.new(1, 0, 0, 30)
LoopButton.Position = UDim2.new(0, 0, 0, 0)
LoopButton.Text = "Loop"
LoopButton.BackgroundColor3 = Color3.fromRGB(0, 200, 0)
LoopButton.TextColor3 = Color3.fromRGB(255, 255, 255)

LoopInfButton.Parent = TeleportFrame
LoopInfButton.Size = UDim2.new(1, 0, 0, 30)
LoopInfButton.Position = UDim2.new(0, 0, 0, 35)
LoopInfButton.Text = "Loop Infinito"
LoopInfButton.BackgroundColor3 = Color3.fromRGB(200, 0, 0)
LoopInfButton.TextColor3 = Color3.fromRGB(255, 255, 255)

local function loop()
    while true do
        for i = 1, 20 do
            local checkpoint = workspace.EventPartFolder:FindFirstChild(tostring(i))
            if checkpoint then
                game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", checkpoint)
            end
            task.wait()
        end
    end
end

local function loopInf()
    while true do
        for i = 1, 20 do
            game:GetService("ReplicatedStorage").RemoteMessenger.SendData:FireServer("CheckPointUpdate", workspace.EventPartFolder[tostring(i)])
            task.wait()
        end
    end
end

LoopButton.MouseButton1Click:Connect(loop)
LoopInfButton.MouseButton1Click:Connect(loopInf)

CreditsButton.MouseButton1Click:Connect(function()
    CreditsFrame.Visible = true
    TeleportFrame.Visible = false
end)

TeleportButton.MouseButton1Click:Connect(function()
    CreditsFrame.Visible = false
    TeleportFrame.Visible = true
end)

CloseButton.MouseButton1Click:Connect(function()
    ScreenGui:Destroy()
end)
