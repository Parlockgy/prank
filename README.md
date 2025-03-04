local Players = game:GetService("Players")
local player = Players.LocalPlayer
local PlayerGui = player:WaitForChild("PlayerGui")
local Lighting = game:GetService("Lighting")

-- Criando a ScreenGui no PlayerGui do jogador
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Parent = PlayerGui

-- Criando a Frame e o Botão
local Frame = Instance.new("Frame")
local TextButton = Instance.new("TextButton")

Frame.Name = "SkyChangerFrame"
Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
Frame.BorderColor3 = Color3.fromRGB(0, 0, 0)
Frame.BorderSizePixel = 0
Frame.Position = UDim2.new(0.5, -75, 0.8, -25)
Frame.Size = UDim2.new(0, 150, 0, 50)

TextButton.Parent = Frame
TextButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
TextButton.BorderColor3 = Color3.fromRGB(0, 0, 0)
TextButton.BorderSizePixel = 0
TextButton.Size = UDim2.new(1, 0, 1, 0)
TextButton.Font = Enum.Font.SourceSans
TextButton.Text = "ChangeSky"
TextButton.TextColor3 = Color3.fromRGB(0, 0, 0)
TextButton.TextSize = 14

-- Função para remover o Sky atual
local function removeSky()
    for _, obj in pairs(Lighting:GetChildren()) do
        if obj:IsA("Sky") then
            obj:Destroy()
        end
    end
end

-- Função para criar um novo Sky
local function createSky()
    removeSky()

    local newSky = Instance.new("Sky")
    newSky.Name = "Teste"
    newSky.Parent = Lighting

    -- Definindo todos os IDs
    local assetId = "rbxassetid://117040568125131"
    newSky.SkyboxBk = assetId
    newSky.SkyboxDn = assetId
    newSky.SkyboxFt = assetId
    newSky.SkyboxLf = assetId
    newSky.SkyboxRt = assetId
    newSky.SkyboxUp = assetId
    newSky.SunTextureId = "0"
end

-- Conectar o botão para mudar o Sky
TextButton.MouseButton1Click:Connect(createSky)
