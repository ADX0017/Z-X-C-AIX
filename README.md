local Players = game:GetService("Players")
local UserInputService = game:GetService("UserInputService")
local VirtualInputManager = game:GetService("VirtualInputManager")
local player = Players.LocalPlayer

local screenGui = Instance.new("ScreenGui", player:WaitForChild("PlayerGui"))
screenGui.Name = "AutoKeyGUI"

local toggleButton = Instance.new("TextButton", screenGui)
toggleButton.Size = UDim2.new(0, 150, 0, 50)
toggleButton.Position = UDim2.new(1, -160, 0.4, 0)
toggleButton.AnchorPoint = Vector2.new(0, 0)
toggleButton.Text = "เริ่มกด ZXC"
toggleButton.BackgroundColor3 = Color3.fromRGB(60, 180, 255)
toggleButton.TextColor3 = Color3.new(1,1,1)
toggleButton.Font = Enum.Font.GothamBold
toggleButton.TextSize = 18
toggleButton.BorderSizePixel = 0
toggleButton.AutoButtonColor = true

local isRunning = false

local function pressKey(key)
    VirtualInputManager:SendKeyEvent(true, key, false, game)
    wait(0.05)
    VirtualInputManager:SendKeyEvent(false, key, false, game)
end

task.spawn(function()
    while true do
        if isRunning then
            pressKey(Enum.KeyCode.Z)
            pressKey(Enum.KeyCode.X)
            pressKey(Enum.KeyCode.C)
        end
        wait(0.2)
    end
end)

toggleButton.MouseButton1Click:Connect(function()
    isRunning = not isRunning
    toggleButton.Text = isRunning and "หยุดกด ZXC" or "เริ่มกด ZXC"
    toggleButton.BackgroundColor3 = isRunning and Color3.fromRGB(255, 80, 80) or Color3.fromRGB(60, 180, 255)
end)
