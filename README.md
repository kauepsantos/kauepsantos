local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Players = game:GetService("Players")

local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

local gui = Instance.new("ScreenGui")
gui.Name = "AddMoneyGui"
gui.Parent = playerGui

local frame = Instance.new("Frame")
frame.Name = "AddMoneyFrame"
frame.Size = UDim2.new(0, 300, 0, 200)
frame.Position = UDim2.new(0.5, -150, 0.5, -100)
frame.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
frame.Draggable = true
frame.Active = true
frame.Parent = gui

local inputBox = Instance.new("TextBox")
inputBox.Name = "InputBox"
inputBox.Size = UDim2.new(0, 200, 0, 50)
inputBox.Position = UDim2.new(0.5, -100, 0, 20)
inputBox.PlaceholderText = "Digite a quantia"
inputBox.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
inputBox.TextColor3 = Color3.fromRGB(0, 0, 0)
inputBox.Parent = frame

local addButton = Instance.new("TextButton")
addButton.Name = "AddButton"
addButton.Text = "Adicionar Dinheiro"
addButton.Size = UDim2.new(0, 200, 0, 50)
addButton.Position = UDim2.new(0.5, -100, 0, 90)
addButton.BackgroundColor3 = Color3.fromRGB(70, 130, 180)
addButton.TextColor3 = Color3.fromRGB(255, 255, 255)
addButton.Font = Enum.Font.SourceSansBold
addButton.TextSize = 18
addButton.Parent = frame

local adminMoneyButton = Instance.new("TextButton")
adminMoneyButton.Name = "AdminMoneyButton"
adminMoneyButton.Text = "Admin Money (tora isme)"
adminMoneyButton.Size = UDim2.new(0, 200, 0, 50)
adminMoneyButton.Position = UDim2.new(0.5, -100, 0, 150)
adminMoneyButton.BackgroundColor3 = Color3.fromRGB(34, 139, 34)
adminMoneyButton.TextColor3 = Color3.fromRGB(255, 255, 255)
adminMoneyButton.Font = Enum.Font.SourceSansBold
adminMoneyButton.TextSize = 18
adminMoneyButton.Parent = frame

-- Conecta o botão de adicionar dinheiro
addButton.MouseButton1Click:Connect(function()
    local amount = tonumber(inputBox.Text)
    if amount and amount > 0 then
        local args = { amount }
        ReplicatedStorage:WaitForChild("dataTransfer"):FireServer(unpack(args))
    else
        warn("Por favor, insira uma quantia válida!")
    end
end)

-- Conecta o botão "Admin Money (tora isme)" para adicionar a quantidade específica sem exibir a mensagem
adminMoneyButton.MouseButton1Click:Connect(function()
    local adminAmount = 9473996838
    local args = { adminAmount }
    ReplicatedStorage:WaitForChild("dataTransfer"):FireServer(unpack(args))
end)
