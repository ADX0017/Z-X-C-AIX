local Players = game:GetService("Players")
local player = Players.LocalPlayer

repeat wait() until player:FindFirstChild("PlayerGui")

local gui = Instance.new("ScreenGui")
gui.Name = "AutoKeyGUI"
gui.ResetOnSpawn = false
gui.Parent = player:WaitForChild("PlayerGui")

local button = Instance.new("TextButton")
button.Size = UDim2.new(0, 100, 0, 50)
button.Position = UDim2.new(1, -110, 0.5, -25)
button.Text = "Start"
button.BackgroundColor3 = Color3.fromRGB(50, 200, 50)
button.TextColor3 = Color3.new(1, 1, 1)
button.Font = Enum.Font.SourceSansBold
button.TextSize = 20
button.Parent = gui

local running = false
local keys = {"Z", "X", "C"}

local function useSkill(key)
	print("ใช้สกิล: " .. key)
end

task.spawn(function()
	while true do
		task.wait(0.3)
		if running then
			for _, key in ipairs(keys) do
				useSkill(key)
			end
		end
	end
end)

button.MouseButton1Click:Connect(function()
	running = not running
	button.Text = running and "Stopv1.2" or "Startv1.2"
	button.BackgroundColor3 = running and Color3.fromRGB(200, 50, 50) or Color3.fromRGB(50, 200, 50)
end)
