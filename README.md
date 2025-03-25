local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoidRootPart = character:FindFirstChild("HumanoidRootPart")

if humanoidRootPart then
    for _, part in pairs(character:GetDescendants()) do
        if part:IsA("BasePart") then
            part.CanCollide = false
        end
    end
    humanoidRootPart.CFrame = humanoidRootPart.CFrame * CFrame.new(0, -100, 0)
end
