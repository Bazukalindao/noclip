local player = game.Players.LocalPlayer
local playerGui = player:FindFirstChild("PlayerGui")
if not playerGui then return end

local screenGui = Instance.new("ScreenGui")
screenGui.Parent = playerGui

local frame = Instance.new("Frame")
frame.Size = UDim2.new(0, 300, 0, 150)
frame.Position = UDim2.new(0.5, -150, 0.3, 0)
frame.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
frame.BorderSizePixel = 2
frame.Draggable = true
frame.Active = true
frame.Parent = screenGui

local closeButton = Instance.new("TextButton")
closeButton.Size = UDim2.new(0, 30, 0, 30)
closeButton.Position = UDim2.new(1, -35, 0, 5)
closeButton.Text = "X"
closeButton.TextColor3 = Color3.fromRGB(255, 255, 255)
closeButton.BackgroundColor3 = Color3.fromRGB(200, 0, 0)
closeButton.Parent = frame

local textBox = Instance.new("TextBox")
textBox.Size = UDim2.new(0.8, 0, 0, 40)
textBox.Position = UDim2.new(0.1, 0, 0.2, 0)
textBox.PlaceholderText = "Digite o nick do jogador..."
textBox.Text = ""
textBox.TextColor3 = Color3.fromRGB(255, 255, 255)
textBox.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
textBox.Parent = frame

local button = Instance.new("TextButton")
button.Size = UDim2.new(0.8, 0, 0, 40)
button.Position = UDim2.new(0.1, 0, 0.6, 0)
button.Text = "Teleportar"
button.TextColor3 = Color3.fromRGB(255, 255, 255)
button.BackgroundColor3 = Color3.fromRGB(0, 170, 255)
button.Parent = frame

local function teleportToPlayer(targetName)
    local character = player.Character
    local targetPlayer = game.Players:FindFirstChild(targetName)

    if character and targetPlayer and targetPlayer.Character then
        local humanoidRootPart = character:FindFirstChild("HumanoidRootPart")
        local targetRootPart = targetPlayer.Character:FindFirstChild("HumanoidRootPart")

        if humanoidRootPart and targetRootPart then
            humanoidRootPart.CFrame = targetRootPart.CFrame + Vector3.new(0, 2, 0)
        end
    end
end

button.MouseButton1Click:Connect(function()
    local targetName = textBox.Text
    if targetName and targetName ~= "" then
        teleportToPlayer(targetName)
    end
end)

closeButton.MouseButton1Click:Connect(function()
    screenGui:Destroy()
end)
