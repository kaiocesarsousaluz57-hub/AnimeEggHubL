local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local UserInputService = game:GetService("UserInputService")
local TweenService = game:GetService("TweenService")
local LP = Players.LocalPlayer

local Config = { Speed = 16, SpeedOn = false }

local C = {
    BG = Color3.fromRGB(18,18,22),
    Sec = Color3.fromRGB(28,28,34),
    Acc = Color3.fromRGB(138,43,226),
    Txt = Color3.fromRGB(240,240,240),
    Sub = Color3.fromRGB(150,150,160),
    No = Color3.fromRGB(240,70,70),
}

local Gui = Instance.new("ScreenGui")
Gui.Name = "Menu"
Gui.ResetOnSpawn = false
Gui.Parent = game:GetService("CoreGui")

local Main = Instance.new("Frame")
Main.Size = UDim2.new(0, 420, 0, 260)
Main.Position = UDim2.new(0.5, -210, 0.5, -130)
Main.BackgroundColor3 = C.BG
Main.BorderSizePixel = 0
Main.Active = true
Main.Draggable = true
Main.Parent = Gui

Instance.new("UICorner", Main).CornerRadius = UDim.new(0, 12)
local stroke = Instance.new("UIStroke", Main)
stroke.Color = C.Acc
stroke.Thickness = 1.5
stroke.Transparency = 0.3

local Header = Instance.new("Frame")
Header.Size = UDim2.new(1, 0, 0, 50)
Header.BackgroundColor3 = C.Sec
Header.BorderSizePixel = 0
Header.Parent = Main
Instance.new("UICorner", Header).CornerRadius = UDim.new(0, 12)

local fix = Instance.new("Frame", Header)
fix.Size = UDim2.new(1, 0, 0, 12)
fix.Position = UDim2.new(0, 0, 1, -12)
fix.BackgroundColor3 = C.Sec
fix.BorderSizePixel = 0

local Title = Instance.new("TextLabel")
Title.Size = UDim2.new(1, -60, 1, 0)
Title.Position = UDim2.new(0, 15, 0, 0)
Title.BackgroundTransparency = 1
Title.Text = "⚡ MENU"
Title.TextColor3 = C.Txt
Title.TextSize = 16
Title.Font = Enum.Font.GothamBold
Title.TextXAlignment = Enum.TextXAlignment.Left
Title.Parent = Header

local Close = Instance.new("TextButton")
Close.Size = UDim2.new(0, 28, 0, 28)
Close.Position = UDim2.new(1, -36, 0, 11)
Close.BackgroundColor3 = C.No
Close.BackgroundTransparency = 0.9
Close.Text = "✕"
Close.TextColor3 = C.No
Close.Font = Enum.Font.GothamBold
Close.Parent = Header
Instance.new("UICorner", Close).CornerRadius = UDim.new(0, 8)
Close.MouseButton1Click:Connect(function() Gui:Destroy() end)

local Content = Instance.new("Frame")
Content.Size = UDim2.new(1, -24, 1, -62)
Content.Position = UDim2.new(0, 12, 0, 56)
Content.BackgroundTransparency = 1
Content.Parent = Main

local layout = Instance.new("UIListLayout", Content)
layout.Padding = UDim.new(0, 8)
layout.SortOrder = Enum.SortOrder.LayoutOrder

-- Toggle Velocidade
local SpeedBox = Instance.new("Frame")
SpeedBox.Size = UDim2.new(1, 0, 0, 55)
SpeedBox.BackgroundColor3 = C.Sec
SpeedBox.BackgroundTransparency = 0.3
SpeedBox.BorderSizePixel = 0
SpeedBox.Parent = Content
Instance.new("UICorner", SpeedBox).CornerRadius = UDim.new(0, 10)

local SpeedLabel = Instance.new("TextLabel")
SpeedLabel.Size = UDim2.new(0, 200, 0, 20)
SpeedLabel.Position = UDim2.new(0, 15, 0, 10)
SpeedLabel.BackgroundTransparency = 1
SpeedLabel.Text = "Ativar Velocidade"
SpeedLabel.TextColor3 = C.Txt
SpeedLabel.TextSize = 14
SpeedLabel.Font = Enum.Font.GothamSemibold
SpeedLabel.TextXAlignment = Enum.TextXAlignment.Left
SpeedLabel.Parent = SpeedBox

local SpeedDesc = Instance.new("TextLabel")
SpeedDesc.Size = UDim2.new(0, 250, 0, 16)
SpeedDesc.Position = UDim2.new(0, 15, 0, 30)
SpeedDesc.BackgroundTransparency = 1
SpeedDesc.Text = "Modifica WalkSpeed"
SpeedDesc.TextColor3 = C.Sub
SpeedDesc.TextSize = 11
SpeedDesc.Font = Enum.Font.Gotham
SpeedDesc.TextXAlignment = Enum.TextXAlignment.Left
SpeedDesc.Parent = SpeedBox

local ToggleBtn = Instance.new("TextButton")
ToggleBtn.Size = UDim2.new(0, 50, 0, 26)
ToggleBtn.Position = UDim2.new(1, -65, 0.5, -13)
ToggleBtn.BackgroundColor3 = Color3.fromRGB(45, 45, 55)
ToggleBtn.Text = ""
ToggleBtn.AutoButtonColor = false
ToggleBtn.Parent = SpeedBox
Instance.new("UICorner", ToggleBtn).CornerRadius = UDim.new(1, 0)

local Dot = Instance.new("Frame")
Dot.Size = UDim2.new(0, 20, 0, 20)
Dot.Position = UDim2.new(0, 3, 0.5, -10)
Dot.BackgroundColor3 = Color3.fromRGB(180, 180, 190)
Dot.BorderSizePixel = 0
Dot.Parent = ToggleBtn
Instance.new("UICorner", Dot).CornerRadius = UDim.new(1, 0)

-- Toggle Anti-Ban
local BanBox = Instance.new("Frame")
BanBox.Size = UDim2.new(1, 0, 0, 55)
BanBox.BackgroundColor3 = C.Sec
BanBox.BackgroundTransparency = 0.3
BanBox.BorderSizePixel = 0
BanBox.Parent = Content
Instance.new("UICorner", BanBox).CornerRadius = UDim.new(0, 10)

local BanLabel = Instance.new("TextLabel")
BanLabel.Size = UDim2.new(0, 200, 0, 20)
BanLabel.Position = UDim2.new(0, 15, 0, 10)
BanLabel.BackgroundTransparency = 1
BanLabel.Text = "Anti-Ban"
BanLabel.TextColor3 = C.Txt
BanLabel.TextSize = 14
BanLabel.Font = Enum.Font.GothamSemibold
BanLabel.TextXAlignment = Enum.TextXAlignment.Left
BanLabel.Parent = BanBox

local BanDesc = Instance.new("TextLabel")
BanDesc.Size = UDim2.new(0, 250, 0, 16)
BanDesc.Position = UDim2.new(0, 15, 0, 30)
BanDesc.BackgroundTransparency = 1
BanDesc.Text = "Remove anti-cheat local"
BanDesc.TextColor3 = C.Sub
BanDesc.TextSize = 11
BanDesc.Font = Enum.Font.Gotham
BanDesc.TextXAlignment = Enum.TextXAlignment.Left
BanDesc.Parent = BanBox

local BanToggle = Instance.new("TextButton")
BanToggle.Size = UDim2.new(0, 50, 0, 26)
BanToggle.Position = UDim2.new(1, -65, 0.5, -13)
BanToggle.BackgroundColor3 = Color3.fromRGB(45, 45, 55)
BanToggle.Text = ""
BanToggle.AutoButtonColor = false
BanToggle.Parent = BanBox
Instance.new("UICorner", BanToggle).CornerRadius = UDim.new(1, 0)

local BanDot = Instance.new("Frame")
BanDot.Size = UDim2.new(0, 20, 0, 20)
BanDot.Position = UDim2.new(0, 3, 0.5, -10)
BanDot.BackgroundColor3 = Color3.fromRGB(180, 180, 190)
BanDot.BorderSizePixel = 0
BanDot.Parent = BanToggle
Instance.new("UICorner", BanDot).CornerRadius = UDim.new(1, 0)

-- Slider Velocidade
local SliderBox = Instance.new("Frame")
SliderBox.Size = UDim2.new(1, 0, 0, 55)
SliderBox.BackgroundColor3 = C.Sec
SliderBox.BackgroundTransparency = 0.3
SliderBox.BorderSizePixel = 0
SliderBox.Parent = Content
Instance.new("UICorner", SliderBox).CornerRadius = UDim.new(0, 10)

local SliderLabel = Instance.new("TextLabel")
SliderLabel.Size = UDim2.new(0, 200, 0, 20)
SliderLabel.Position = UDim2.new(0, 15, 0, 10)
SliderLabel.BackgroundTransparency = 1
SliderLabel.Text = "Velocidade: 16"
SliderLabel.TextColor3 = C.Txt
SliderLabel.TextSize = 14
SliderLabel.Font = Enum.Font.GothamSemibold
SliderLabel.TextXAlignment = Enum.TextXAlignment.Left
SliderLabel.Parent = SliderBox

local SliderBG = Instance.new("TextButton")
SliderBG.Size = UDim2.new(1, -30, 0, 8)
SliderBG.Position = UDim2.new(0, 15, 0, 40)
SliderBG.BackgroundColor3 = Color3.fromRGB(45, 45, 55)
SliderBG.Text = ""
SliderBG.AutoButtonColor = false
SliderBG.Parent = SliderBox
Instance.new("UICorner", SliderBG).CornerRadius = UDim.new(1, 0)

local Fill = Instance.new("Frame")
Fill.Size = UDim2.new(0, 0, 1, 0)
Fill.BackgroundColor3 = C.Acc
Fill.BorderSizePixel = 0
Fill.Parent = SliderBG
Instance.new("UICorner", Fill).CornerRadius = UDim.new(1, 0)

-- Lógica Velocidade
local SpeedConn
local function SetSpeed(state)
    Config.SpeedOn = state
    if state then
        TweenService:Create(ToggleBtn, TweenInfo.new(0.25), {BackgroundColor3 = C.Acc}):Play()
        TweenService:Create(Dot, TweenInfo.new(0.25), {Position = UDim2.new(1, -23, 0.5, -10), BackgroundColor3 = Color3.new(1,1,1)}):Play()
        if SpeedConn then SpeedConn:Disconnect() end
        SpeedConn = RunService.Heartbeat:Connect(function()
            local char = LP.Character
            local hum = char and char:FindFirstChildOfClass("Humanoid")
            if hum then hum.WalkSpeed = Config.Speed end
        end)
    else
        TweenService:Create(ToggleBtn, TweenInfo.new(0.25), {BackgroundColor3 = Color3.fromRGB(45,45,55)}):Play()
        TweenService:Create(Dot, TweenInfo.new(0.25), {Position = UDim2.new(0, 3, 0.5, -10), BackgroundColor3 = Color3.fromRGB(180,180,190)}):Play()
        if SpeedConn then SpeedConn:Disconnect() SpeedConn = nil end
    end
end

ToggleBtn.MouseButton1Click:Connect(function() SetSpeed(not Config.SpeedOn) end)

-- Lógica Anti-Ban
local BanOn = false
local BanConn
BanToggle.MouseButton1Click:Connect(function()
    BanOn = not BanOn
    if BanOn then
        TweenService:Create(BanToggle, TweenInfo.new(0.25), {BackgroundColor3 = C.Acc}):Play()
        TweenService:Create(BanDot, TweenInfo.new(0.25), {Position = UDim2.new(1, -23, 0.5, -10), BackgroundColor3 = Color3.new(1,1,1)}):Play()
        BanConn = RunService.Heartbeat:Connect(function()
            local char = LP.Character
            if char then
                for _, v in pairs(char:GetDescendants()) do
                    if v:IsA("Script") and v.Name:lower():find("anti") then v:Destroy() end
                end
            end
        end)
    else
        TweenService:Create(BanToggle, TweenInfo.new(0.25), {BackgroundColor3 = Color3.fromRGB(45,45,55)}):Play()
        TweenService:Create(BanDot, TweenInfo.new(0.25), {Position = UDim2.new(0, 3, 0.5, -10), BackgroundColor3 = Color3.fromRGB(180,180,190)}):Play()
        if BanConn then BanConn:Disconnect() BanConn = nil end
    end
end)

-- Slider
local dragging = false
local function UpdateSlider(input)
    local pos = math.clamp((input.Position.X - SliderBG.AbsolutePosition.X) / SliderBG.AbsoluteSize.X, 0, 1)
    local val = math.floor(16 + (200 - 16) * pos)
    Fill.Size = UDim2.new(pos, 0, 1, 0)
    SliderLabel.Text = "Velocidade: " .. val
    Config.Speed = val
end

SliderBG.InputBegan:Connect(function(i)
    if i.UserInputType == Enum.UserInputType.MouseButton1 or i.UserInputType == Enum.UserInputType.Touch then
        dragging = true
        UpdateSlider(i)
    end
end)
SliderBG.InputEnded:Connect(function(i)
    if i.UserInputType == Enum.UserInputType.MouseButton1 or i.UserInputType == Enum.UserInputType.Touch then
        dragging = false
    end
end)
UserInputService.InputChanged:Connect(function(i)
    if dragging and (i.UserInputType == Enum.UserInputType.MouseMovement or i.UserInputType == Enum.UserInputType.Touch) then
        UpdateSlider(i)
    end
end)

-- Animação de entrada
Main.Size = UDim2.new(0, 0, 0, 0)
TweenService:Create(Main, TweenInfo.new(0.4, Enum.EasingStyle.Back, Enum.EasingDirection.Out), {
    Size = UDim2.new(0, 420, 0, 260)
}):Play()
