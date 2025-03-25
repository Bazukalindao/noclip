local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoidRootPart = character:FindFirstChild("HumanoidRootPart")

if humanoidRootPart then
    humanoidRootPart.CFrame = humanoidRootPart.CFrame * CFrame.new(0, -5, 0)
end
