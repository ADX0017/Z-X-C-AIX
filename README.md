local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "AutoKeyGui"
ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

local button = Instance.new("TextButton")
button.Size = UDim2.new(0, 100, 0, 50)
button.Position = UDim2.new(1, -110, 0.5, -25)
button.Text = "Start"
button.Parent = ScreenGui
button.BackgroundColor3 = Color3.fromRGB(50, 200, 50)
button.TextColor3 = Color3.new(1, 1, 1)
button.Font = Enum.Font.SourceSansBold
button.TextSize = 20

local running = false

local UserInputService = game:GetService("UserInputService")

local function pressKey(key)
    UserInputService.InputBegan:Fire({KeyCode = Enum.KeyCode[key], UserInputType = Enum.UserInputType.Keyboard})
    UserInputService.InputEnded:Fire({KeyCode = Enum.KeyCode[key], UserInputType = Enum.UserInputType.Keyboard})
end

task.spawn(function()
    while true do
        wait(0.3)
        if running then
            pressKey("Z")
            pressKey("X")
            pressKey("C")
        end
    end
end)

button.MouseButton1Click:Connect(function()
    running = not running
    button.Text = running and "Stop" or "Start"
    button.BackgroundColor3 = running and Color3.fromRGB(200, 50, 50) or Color3.fromRGB(50, 200, 50)
end)
