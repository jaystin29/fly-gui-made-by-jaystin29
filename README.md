# fly-gui-made-by-jaystin29
a simple fly gui made by jaystin29
local player = game.Players.LocalPlayer

local gui = Instance.new("ScreenGui")
gui.Name = "JaystinSpeedGUI"
gui.ResetOnSpawn = false
gui.Parent = player:WaitForChild("PlayerGui")

-- Colors
local BLACK = Color3.fromRGB(15, 15, 15)
local YELLOW = Color3.fromRGB(255, 200, 0)
local WHITE = Color3.fromRGB(255, 255, 255)

-- Main Frame
local frame = Instance.new("Frame")
frame.Size = UDim2.new(0, 240, 0, 160)
frame.Position = UDim2.new(0.5, -120, 0.5, -80)
frame.BackgroundColor3 = BLACK
frame.BorderSizePixel = 0
frame.Parent = gui

local corner = Instance.new("UICorner")
corner.CornerRadius = UDim.new(0, 12)
corner.Parent = frame

-- Title
local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, -40, 0, 35)
title.Position = UDim2.new(0, 15, 0, 5)
title.BackgroundTransparency = 1
title.Text = "CRDTS: Jaystin"
title.TextColor3 = YELLOW
title.TextSize = 20
title.Font = Enum.Font.GothamBold
title.TextXAlignment = Enum.TextXAlignment.Left
title.Parent = frame

-- Close Button
local closeButton = Instance.new("TextButton")
closeButton.Size = UDim2.new(0, 30, 0, 30)
closeButton.Position = UDim2.new(1, -35, 0, 5)
closeButton.BackgroundColor3 = YELLOW
closeButton.Text = "X"
closeButton.TextColor3 = BLACK
closeButton.Font = Enum.Font.GothamBold
closeButton.TextSize = 16
closeButton.Parent = frame

local closeCorner = Instance.new("UICorner")
closeCorner.CornerRadius = UDim.new(0, 8)
closeCorner.Parent = closeButton

-- Speed Box
local speedBox = Instance.new("TextBox")
speedBox.Size = UDim2.new(0, 200, 0, 40)
speedBox.Position = UDim2.new(0, 20, 0, 50)
speedBox.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
speedBox.TextColor3 = WHITE
speedBox.PlaceholderColor3 = Color3.fromRGB(150, 150, 150)
speedBox.PlaceholderText = "Enter speed"
speedBox.Text = "16"
speedBox.TextSize = 16
speedBox.Font = Enum.Font.Gotham
speedBox.Parent = frame

local boxCorner = Instance.new("UICorner")
boxCorner.CornerRadius = UDim.new(0, 8)
boxCorner.Parent = speedBox

-- Change Speed Button
local button = Instance.new("TextButton")
button.Size = UDim2.new(0, 200, 0, 40)
button.Position = UDim2.new(0, 20, 0, 105)
button.BackgroundColor3 = YELLOW
button.Text = "CHANGE SPEED"
button.TextColor3 = BLACK
button.TextSize = 15
button.Font = Enum.Font.GothamBold
button.Parent = frame

local buttonCorner = Instance.new("UICorner")
buttonCorner.CornerRadius = UDim.new(0, 8)
buttonCorner.Parent = button

-- Floating Bubble
local bubble = Instance.new("TextButton")
bubble.Size = UDim2.new(0, 55, 0, 55)
bubble.Position = UDim2.new(0, 20, 0.5, -25)
bubble.BackgroundColor3 = BLACK
bubble.Text = "⚡"
bubble.TextColor3 = YELLOW
bubble.TextSize = 25
bubble.Visible = false
bubble.Parent = gui

local bubbleCorner = Instance.new("UICorner")
bubbleCorner.CornerRadius = UDim.new(1, 0)
bubbleCorner.Parent = bubble

-- Change Speed
button.MouseButton1Click:Connect(function()
	local speed = tonumber(speedBox.Text)
	local character = player.Character
	local humanoid = character and character:FindFirstChildOfClass("Humanoid")

	if speed and humanoid then
		humanoid.WalkSpeed = speed
	end
end)

-- Close
closeButton.MouseButton1Click:Connect(function()
	frame.Visible = false
	bubble.Visible = true
end)

-- Open
bubble.MouseButton1Click:Connect(function()
	frame.Visible = true
	bubble.Visible = false
end)
