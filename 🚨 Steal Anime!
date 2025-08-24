local Players = game:GetService("Players")
local Workspace = game:GetService("Workspace")
local CoreGui = game:GetService("CoreGui")

local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local hrp = character:WaitForChild("HumanoidRootPart")

-- GUI Setup
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "TeleportGUI"
screenGui.ResetOnSpawn = false
screenGui.Parent = CoreGui

local mainFrame = Instance.new("Frame")
mainFrame.Size = UDim2.new(0, 315, 0, 350)
mainFrame.Position = UDim2.new(0.7, 0, 0.3, 0)
mainFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
mainFrame.BorderSizePixel = 2
mainFrame.BorderColor3 = Color3.fromRGB(80, 80, 80)
mainFrame.Active = true
mainFrame.Draggable = true
mainFrame.Parent = screenGui

-- Title Bar
local titleBar = Instance.new("Frame")
titleBar.Size = UDim2.new(1, 0, 0, 35)
titleBar.BackgroundColor3 = Color3.fromRGB(90, 0, 150)
titleBar.BorderSizePixel = 0
titleBar.Parent = mainFrame

local titleLabel = Instance.new("TextLabel")
titleLabel.Size = UDim2.new(1, -90, 1, 0)
titleLabel.Position = UDim2.new(0, 5, 0, 0)
titleLabel.BackgroundTransparency = 1
titleLabel.Text = "Teleportar para Base"
titleLabel.TextColor3 = Color3.new(1, 1, 1)
titleLabel.Font = Enum.Font.GothamBold
titleLabel.TextSize = 20
titleLabel.TextXAlignment = Enum.TextXAlignment.Left
titleLabel.Parent = titleBar

-- Fechar
local closeBtn = Instance.new("TextButton")
closeBtn.Size = UDim2.new(0, 30, 0, 30)
closeBtn.Position = UDim2.new(1, -35, 0, 2)
closeBtn.BackgroundColor3 = Color3.fromRGB(170, 0, 0)
closeBtn.Text = "X"
closeBtn.TextColor3 = Color3.new(1, 1, 1)
closeBtn.Font = Enum.Font.GothamBold
closeBtn.TextSize = 18
closeBtn.Parent = titleBar

closeBtn.MouseButton1Click:Connect(function()
	screenGui:Destroy()
end)

-- Minimizar
local minimizeBtn = Instance.new("TextButton")
minimizeBtn.Size = UDim2.new(0, 30, 0, 30)
minimizeBtn.Position = UDim2.new(1, -105, 0, 2)
minimizeBtn.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
minimizeBtn.Text = "-"
minimizeBtn.TextColor3 = Color3.new(1, 1, 1)
minimizeBtn.Font = Enum.Font.GothamBold
minimizeBtn.TextSize = 18
minimizeBtn.Parent = titleBar

-- Maximizar
local maximizeBtn = Instance.new("TextButton")
maximizeBtn.Size = UDim2.new(0, 30, 0, 30)
maximizeBtn.Position = UDim2.new(1, -70, 0, 2)
maximizeBtn.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
maximizeBtn.Text = "▢"
maximizeBtn.TextColor3 = Color3.new(1, 1, 1)
maximizeBtn.Font = Enum.Font.GothamBold
maximizeBtn.TextSize = 18
maximizeBtn.Parent = titleBar

-- Scrolling Frame
local scrollFrame = Instance.new("ScrollingFrame")
scrollFrame.Size = UDim2.new(1, 0, 1, -35)
scrollFrame.Position = UDim2.new(0, 0, 0, 35)
scrollFrame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
scrollFrame.BorderSizePixel = 0
scrollFrame.CanvasSize = UDim2.new(0, 0, 0, 0)
scrollFrame.ScrollBarThickness = 8
scrollFrame.Visible = true
scrollFrame.Parent = mainFrame

local layout = Instance.new("UIListLayout")
layout.Padding = UDim.new(0, 5)
layout.SortOrder = Enum.SortOrder.LayoutOrder
layout.Parent = scrollFrame

-- Teleporte
local function teleportToBase(index)
	local base = Workspace:FindFirstChild("Bases")
	if base and base:FindFirstChild(tostring(index)) then
		local target = base[tostring(index)]:FindFirstChild("StealCollect2")
		if target and target:IsA("BasePart") then
			hrp.CFrame = target.CFrame + Vector3.new(0, 3, 0)
		else
			warn("StealCollect2 não encontrado na base " .. tostring(index))
		end
	else
		warn("Base " .. tostring(index) .. " não encontrada.")
	end
end

-- Criar botões
for i = 1, 8 do
	local btn = Instance.new("TextButton")
	btn.Size = UDim2.new(1, -10, 0, 40)
	btn.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
	btn.TextColor3 = Color3.new(1, 1, 1)
	btn.Font = Enum.Font.Gotham
	btn.TextSize = 20
	btn.Text = "Ir para Base " .. tostring(i)
	btn.Parent = scrollFrame

	btn.MouseButton1Click:Connect(function()
		teleportToBase(i)
	end)
end

-- Ajustar rolagem automática
scrollFrame.CanvasSize = UDim2.new(0, 0, 0, layout.AbsoluteContentSize.Y)
layout:GetPropertyChangedSignal("AbsoluteContentSize"):Connect(function()
	scrollFrame.CanvasSize = UDim2.new(0, 0, 0, layout.AbsoluteContentSize.Y)
end)

-- Minimizar/maximizar lógica
local isMinimized = false

minimizeBtn.MouseButton1Click:Connect(function()
	scrollFrame.Visible = false
	mainFrame.Size = UDim2.new(0, 315, 0, 35)
	isMinimized = true
end)

maximizeBtn.MouseButton1Click:Connect(function()
	if isMinimized then
		scrollFrame.Visible = true
		mainFrame.Size = UDim2.new(0, 315, 0, 350)
		isMinimized = false
	end
end)
