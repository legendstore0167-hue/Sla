local Players = game:GetService("Players")
local localPlayer = Players.LocalPlayer
local gui = Instance.new("ScreenGui")
gui.Parent = localPlayer:WaitForChild("PlayerGui")
gui.ResetOnSpawn = false


local frame = Instance.new("Frame", gui)
frame.Size = UDim2.new(0, 300, 0, 160)
frame.Position = UDim2.new(0.5, -150, 0.5, -80)
frame.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
frame.BorderSizePixel = 0


local grad = Instance.new("UIGradient", frame)
grad.Color = ColorSequence.new{
    ColorSequenceKeypoint.new(0, Color3.fromRGB(0, 170, 255)),
    ColorSequenceKeypoint.new(1, Color3.fromRGB(0, 90, 255))
}
grad.Rotation = 45


local corner = Instance.new("UICorner", frame)
corner.CornerRadius = UDim.new(0, 20)


frame.Active = true
frame.Draggable = true


local title = Instance.new("TextLabel", frame)
title.Size = UDim2.new(1, 0, 0, 40)
title.Position = UDim2.new(0, 0, 0, 0)
title.BackgroundTransparency = 1
title.TextColor3 = Color3.fromRGB(255, 255, 255)
title.TextSize = 26
title.Font = Enum.Font.GothamBold
title.Text = "💰 Red Hub"


local btn = Instance.new("TextButton", frame)
btn.Size = UDim2.new(0.7, 0, 0, 50)
btn.Position = UDim2.new(0.15, 0, 0.5, -25)
btn.BackgroundColor3 = Color3.fromRGB(0, 150, 255)
btn.TextColor3 = Color3.fromRGB(255, 255, 255)
btn.TextSize = 22
btn.Font = Enum.Font.GothamSemibold
btn.Text = "Instant Steal"
local btnCorner = Instance.new("UICorner", btn)
btnCorner.CornerRadius = UDim.new(0, 15)


local note = Instance.new("TextLabel", frame)
note.Size = UDim2.new(1, 0, 0, 30)
note.Position = UDim2.new(0, 0, 1, -35)
note.BackgroundTransparency = 1
note.TextColor3 = Color3.fromRGB(0, 255, 0)
note.TextSize = 18
note.Font = Enum.Font.Gotham
note.Text = ""


btn.MouseButton1Click:Connect(function()
    local spawnPart
    for _, plot in pairs(workspace.Plots:GetChildren()) do
        if plot:FindFirstChild("PlotSign") and plot.PlotSign:FindFirstChild("SurfaceGui") then
            local surfaceGui = plot.PlotSign.SurfaceGui
            if surfaceGui:FindFirstChild("Frame") and surfaceGui.Frame:FindFirstChild("TextLabel") then
                local textLabel = surfaceGui.Frame.TextLabel
                if textLabel.Text == localPlayer.DisplayName.."'s Base" then
                    spawnPart = surfaceGui.Parent.Parent:FindFirstChild("Spawn")
                    break
                end
            end
        end
    end


    if not spawnPart then
        note.Text = "Base not found"
        return
    end


    local char = localPlayer.Character or localPlayer.CharacterAdded:Wait()
    local hrp = char:WaitForChild("HumanoidRootPart")
    local humanoid = char:FindFirstChildOfClass("Humanoid")
    local target = spawnPart.CFrame + Vector3.new(0, 2, 0)


    for i = 1, 20 do
        hrp.CFrame = target
        task.wait()
    end


    humanoid.PlatformStand = true
    humanoid.AutoRotate = false
    hrp.AssemblyLinearVelocity = Vector3.new(0,0,0)
    hrp.AssemblyAngularVelocity = Vector3.new(0,0,0)


    local start = tick()
    while tick() - start < 2 do
        local x = (math.random() - 0.5) * 0.1
        local y = (math.random() - 0.5) * 0.1
        local z = (math.random() - 0.5) * 0.1
        hrp.CFrame = target * CFrame.Angles(x, y, z)
        task.wait(0.05)
    end


    humanoid.PlatformStand = false
    humanoid.AutoRotate = true
    note.Text = "Teleported to base!"
end)

                local textLabel = surfaceGui.Frame.TextLabel
                if textLabel.Text == localPlayer.DisplayName.."'s Base" then
                    spawnPart = surfaceGui.Parent.Parent:FindFirstChild("Spawn")
                    break
                end
            end
        end
    end


    if not spawnPart then
        note.Text = "Base not found"
        return
    end


    local char = localPlayer.Character or localPlayer.CharacterAdded:Wait()
    local hrp = char:WaitForChild("HumanoidRootPart")
    local humanoid = char:FindFirstChildOfClass("Humanoid")
    local target = spawnPart.CFrame + Vector3.new(0, 2, 0)


    for i = 1, 20 do
        hrp.CFrame = target
        task.wait()
    end


    humanoid.PlatformStand = true
    humanoid.AutoRotate = false
    hrp.AssemblyLinearVelocity = Vector3.new(0,0,0)
    hrp.AssemblyAngularVelocity = Vector3.new(0,0,0)


    local start = tick()
    while tick() - start < 2 do
        local x = (math.random() - 0.5) * 0.1
        local y = (math.random() - 0.5) * 0.1
        local z = (math.random() - 0.5) * 0.1
        hrp.CFrame = target * CFrame.Angles(x, y, z)
        task.wait(0.05)
    end


    humanoid.PlatformStand = false
    humanoid.AutoRotate = true
    note.Text = "Teleported to base!"
end)

