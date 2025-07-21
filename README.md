-- 创建主屏幕GUI
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "PremiumUI"
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

-- 创建背景光晕效果
local Glow = Instance.new("ImageLabel")
Glow.Name = "GlowEffect"
Glow.Size = UDim2.new(1, 100, 1, 100)
Glow.Position = UDim2.new(0, -50, 0, -50)
Glow.BackgroundTransparency = 1
Glow.Image = "rbxassetid://5027830937"
Glow.ImageColor3 = Color3.fromRGB(50, 30, 80)
Glow.ScaleType = Enum.ScaleType.Slice
Glow.SliceCenter = Rect.new(100, 100, 100, 100)
Glow.SliceScale = 0.05
Glow.Parent = ScreenGui

-- 创建主框架
local MainFrame = Instance.new("Frame")
MainFrame.Name = "MainFrame"
MainFrame.Size = UDim2.new(0, 400, 0, 320)
MainFrame.Position = UDim2.new(0.5, -200, 0.5, -160)
MainFrame.AnchorPoint = Vector2.new(0.5, 0.5)
MainFrame.BackgroundColor3 = Color3.fromRGB(20, 15, 30)
MainFrame.BackgroundTransparency = 0.1
MainFrame.BorderSizePixel = 0
MainFrame.ClipsDescendants = true
MainFrame.Parent = ScreenGui

-- 添加高级圆角
local UICorner = Instance.new("UICorner")
UICorner.CornerRadius = UDim.new(0, 16)
UICorner.Parent = MainFrame

-- 添加内发光效果
local InnerGlow = Instance.new("ImageLabel")
InnerGlow.Name = "InnerGlow"
InnerGlow.Size = UDim2.new(1, 0, 1, 0)
InnerGlow.Position = UDim2.new(0, 0, 0, 0)
InnerGlow.BackgroundTransparency = 1
InnerGlow.Image = "rbxassetid://5027830937"
InnerGlow.ImageColor3 = Color3.fromRGB(100, 60, 150)
InnerGlow.ScaleType = Enum.ScaleType.Slice
InnerGlow.SliceCenter = Rect.new(100, 100, 100, 100)
InnerGlow.SliceScale = 0.05
InnerGlow.Parent = MainFrame

-- 添加背景粒子效果
local Particles = Instance.new("Frame")
Particles.Name = "Particles"
Particles.Size = UDim2.new(1, 0, 1, 0)
Particles.BackgroundTransparency = 1
Particles.Parent = MainFrame

-- 创建粒子
for i = 1, 20 do
    local particle = Instance.new("Frame")
    particle.Name = "Particle_"..i
    particle.Size = UDim2.new(0, math.random(2, 4), 0, math.random(2, 4))
    particle.Position = UDim2.new(0, math.random(0, 400), 0, math.random(0, 320))
    particle.BackgroundColor3 = Color3.fromRGB(150 + math.random(0, 50), 100 + math.random(0, 50), 200 + math.random(0, 50))
    particle.BackgroundTransparency = 0.7
    particle.BorderSizePixel = 0
    particle.Parent = Particles
    
    spawn(function()
        while true do
            particle:TweenPosition(
                UDim2.new(0, math.random(0, 400), 0, math.random(0, 320)),
                Enum.EasingDirection.InOut,
                Enum.EasingStyle.Quad,
                math.random(3, 7),
                true
            )
            wait(math.random(5, 10))
        end
    end)
end

-- 添加标题
local TitleLabel = Instance.new("TextLabel")
TitleLabel.Name = "TitleLabel"
TitleLabel.Size = UDim2.new(1, -60, 0, 60)
TitleLabel.Position = UDim2.new(0, 20, 0, 10)
TitleLabel.BackgroundTransparency = 1
TitleLabel.Text = "qq1104542829\nQ群985931130"
TitleLabel.TextColor3 = Color3.fromRGB(220, 220, 255)
TitleLabel.Font = Enum.Font.GothamBlack
TitleLabel.TextSize = 22
TitleLabel.TextWrapped = true
TitleLabel.TextXAlignment = Enum.TextXAlignment.Left
TitleLabel.TextYAlignment = Enum.TextYAlignment.Top
TitleLabel.Parent = MainFrame

-- 添加LOGO
local Logo = Instance.new("ImageLabel")
Logo.Name = "Logo"
Logo.Size = UDim2.new(0, 80, 0, 80)
Logo.Position = UDim2.new(0.5, -40, 0, -90)
Logo.BackgroundTransparency = 1
Logo.Image = "rbxassetid://114955888794605"
Logo.ImageColor3 = Color3.fromRGB(220, 220, 255)
Logo.ZIndex = 2
Logo.Parent = ScreenGui

-- 添加LOGO光晕
local LogoGlow = Instance.new("ImageLabel")
LogoGlow.Name = "LogoGlow"
LogoGlow.Size = UDim2.new(0, 120, 0, 120)
LogoGlow.Position = UDim2.new(0.5, -60, 0, -110)
LogoGlow.BackgroundTransparency = 1
LogoGlow.Image = "rbxassetid://5027830937"
LogoGlow.ImageColor3 = Color3.fromRGB(100, 60, 150)
LogoGlow.ScaleType = Enum.ScaleType.Slice
LogoGlow.SliceCenter = Rect.new(100, 100, 100, 100)
LogoGlow.SliceScale = 0.05
LogoGlow.Parent = ScreenGui

-- 创建关闭/收缩按钮
local CloseButton = Instance.new("ImageButton")
CloseButton.Name = "CloseButton"
CloseButton.Size = UDim2.new(0, 36, 0, 36)
CloseButton.Position = UDim2.new(1, -46, 0, 10)
CloseButton.BackgroundColor3 = Color3.fromRGB(40, 30, 60)
CloseButton.BackgroundTransparency = 0.3
CloseButton.Image = "rbxassetid://6031094675"
CloseButton.ImageColor3 = Color3.fromRGB(200, 200, 255)
CloseButton.Parent = MainFrame

-- 关闭按钮圆角
local UICornerClose = Instance.new("UICorner")
UICornerClose.CornerRadius = UDim.new(1, 0)
UICornerClose.Parent = CloseButton

-- 关闭按钮边框
local UIStrokeClose = Instance.new("UIStroke")
UIStrokeClose.Color = Color3.fromRGB(150, 100, 200)
UIStrokeClose.Thickness = 1.5
UIStrokeClose.Transparency = 0.5
UIStrokeClose.Parent = CloseButton

-- 关闭按钮悬停效果
CloseButton.MouseEnter:Connect(function()
    game:GetService("TweenService"):Create(
        CloseButton,
        TweenInfo.new(0.2),
        {BackgroundTransparency = 0.1, ImageColor3 = Color3.fromRGB(255, 180, 100)}
    ):Play()
    game:GetService("TweenService"):Create(
        UIStrokeClose,
        TweenInfo.new(0.2),
        {Transparency = 0.2}
    ):Play()
end)

CloseButton.MouseLeave:Connect(function()
    game:GetService("TweenService"):Create(
        CloseButton,
        TweenInfo.new(0.2),
        {BackgroundTransparency = 0.3, ImageColor3 = Color3.fromRGB(200, 200, 255)}
    ):Play()
    game:GetService("TweenService"):Create(
        UIStrokeClose,
        TweenInfo.new(0.2),
        {Transparency = 0.5}
    ):Play()
end)

-- 创建收缩小球
local MinimizedBall = Instance.new("ImageButton")
MinimizedBall.Name = "MinimizedBall"
MinimizedBall.Size = UDim2.new(0, 50, 0, 50)
MinimizedBall.Position = UDim2.new(1, -60, 0, 0)
MinimizedBall.BackgroundColor3 = Color3.fromRGB(40, 30, 60)
MinimizedBall.BackgroundTransparency = 0.3
MinimizedBall.Image = "rbxassetid://6031094675"
MinimizedBall.ImageColor3 = Color3.fromRGB(200, 200, 255)
MinimizedBall.Rotation = 45
MinimizedBall.Visible = false
MinimizedBall.ZIndex = 3
MinimizedBall.Parent = ScreenGui

-- 小球圆角
local UICornerBall = Instance.new("UICorner")
UICornerBall.CornerRadius = UDim.new(1, 0)
UICornerBall.Parent = MinimizedBall

-- 小球光晕
local BallGlow = Instance.new("ImageLabel")
BallGlow.Name = "BallGlow"
BallGlow.Size = UDim2.new(1, 20, 1, 20)
BallGlow.Position = UDim2.new(0, -10, 0, -10)
BallGlow.BackgroundTransparency = 1
BallGlow.Image = "rbxassetid://5027830937"
BallGlow.ImageColor3 = Color3.fromRGB(100, 60, 150)
BallGlow.ScaleType = Enum.ScaleType.Slice
BallGlow.SliceCenter = Rect.new(100, 100, 100, 100)
BallGlow.SliceScale = 0.05
BallGlow.Parent = MinimizedBall

-- 小球悬停效果
MinimizedBall.MouseEnter:Connect(function()
    game:GetService("TweenService"):Create(
        MinimizedBall,
        TweenInfo.new(0.2),
        {BackgroundTransparency = 0.1, ImageColor3 = Color3.fromRGB(255, 180, 100), Size = UDim2.new(0, 55, 0, 55)}
    ):Play()
end)

MinimizedBall.MouseLeave:Connect(function()
    game:GetService("TweenService"):Create(
        MinimizedBall,
        TweenInfo.new(0.2),
        {BackgroundTransparency = 0.3, ImageColor3 = Color3.fromRGB(200, 200, 255), Size = UDim2.new(0, 50, 0, 50)}
    ):Play()
end)

-- 创建按钮容器
local ButtonsFrame = Instance.new("Frame")
ButtonsFrame.Name = "ButtonsFrame"
ButtonsFrame.Size = UDim2.new(1, -40, 0, 200)
ButtonsFrame.Position = UDim2.new(0, 20, 0, 80)
ButtonsFrame.BackgroundTransparency = 1
ButtonsFrame.Parent = MainFrame

-- 创建按钮样式函数
local function CreateButton(name, text, positionY, colorType)
    local button = Instance.new("TextButton")
    button.Name = name
    button.Size = UDim2.new(1, 0, 0, 50)
    button.Position = UDim2.new(0, 0, 0, positionY)
    
    -- 根据颜色类型设置按钮颜色
    if colorType == "purple" then
        button.BackgroundColor3 = Color3.fromRGB(90, 50, 130)
    else -- orange
        button.BackgroundColor3 = Color3.fromRGB(180, 90, 30)
    end
    
    button.BackgroundTransparency = 0.3
    button.Text = text
    button.TextColor3 = Color3.fromRGB(255, 255, 255)
    button.Font = Enum.Font.GothamBlack
    button.TextSize = 18
    button.AutoButtonColor = false
    button.Parent = ButtonsFrame
    
    local uiCorner = Instance.new("UICorner")
    uiCorner.CornerRadius = UDim.new(0, 12)
    uiCorner.Parent = button
    
    local uiStroke = Instance.new("UIStroke")
    uiStroke.Color = Color3.fromRGB(255, 255, 255)
    uiStroke.Thickness = 1.5
    uiStroke.Transparency = 0.7
    uiStroke.Parent = button
    
    -- 按钮渐变效果
    local gradient = Instance.new("UIGradient")
    gradient.Rotation = 90
    if colorType == "purple" then
        gradient.Color = ColorSequence.new({
            ColorSequenceKeypoint.new(0, Color3.fromRGB(120, 70, 180)),
            ColorSequenceKeypoint.new(1, Color3.fromRGB(70, 40, 110))
        })
    else
        gradient.Color = ColorSequence.new({
            ColorSequenceKeypoint.new(0, Color3.fromRGB(220, 110, 40)),
            ColorSequenceKeypoint.new(1, Color3.fromRGB(150, 70, 20))
        })
    end
    gradient.Parent = button
    
    -- 按钮悬停效果
    button.MouseEnter:Connect(function()
        game:GetService("TweenService"):Create(
            button,
            TweenInfo.new(0.2),
            {BackgroundTransparency = 0.1, TextColor3 = Color3.fromRGB(255, 255, 200)}
        ):Play()
        game:GetService("TweenService"):Create(
            uiStroke,
            TweenInfo.new(0.2),
            {Transparency = 0.2}
        ):Play()
    end)
    
    button.MouseLeave:Connect(function()
        game:GetService("TweenService"):Create(
            button,
            TweenInfo.new(0.2),
            {BackgroundTransparency = 0.3, TextColor3 = Color3.fromRGB(255, 255, 255)}
        ):Play()
        game:GetService("TweenService"):Create(
            uiStroke,
            TweenInfo.new(0.2),
            {Transparency = 0.7}
        ):Play()
    end)
    
    -- 按钮点击效果
    button.MouseButton1Down:Connect(function()
        game:GetService("TweenService"):Create(
            button,
            TweenInfo.new(0.1),
            {Size = UDim2.new(0.98, 0, 0, 48), Position = UDim2.new(0.01, 0, 0, positionY+1)}
        ):Play()
    end)
    
    button.MouseButton1Up:Connect(function()
        game:GetService("TweenService"):Create(
            button,
            TweenInfo.new(0.1),
            {Size = UDim2.new(1, 0, 0, 50), Position = UDim2.new(0, 0, 0, positionY)}
        ):Play()
    end)
    
    return button
end

-- 创建第一个按钮 (橙色)
local Button1 = CreateButton("Button1", "通 用 代 码", 0, "orange")

-- 创建第二个按钮 (紫色)
local Button2 = CreateButton("Button2", "水龙二技能秒中", 60, "purple")

-- 创建第三个按钮 (橙色)
local Button3 = CreateButton("Button3", "画 我", 120, "orange")

-- 创建音乐按钮 (特殊样式)
local MusicButton = Instance.new("TextButton")
MusicButton.Name = "MusicButton"
MusicButton.Size = UDim2.new(1, -40, 0, 40)
MusicButton.Position = UDim2.new(0, 20, 1, -50)
MusicButton.BackgroundColor3 = Color3.fromRGB(50, 40, 70)
MusicButton.BackgroundTransparency = 0.3
MusicButton.Text = "播放音乐 (ID:1838457617)"
MusicButton.TextColor3 = Color3.fromRGB(200, 200, 255)
MusicButton.Font = Enum.Font.GothamBlack
MusicButton.TextSize = 16
MusicButton.AutoButtonColor = false
MusicButton.Parent = MainFrame

-- 音乐按钮圆角
local UICornerMusic = Instance.new("UICorner")
UICornerMusic.CornerRadius = UDim.new(0, 10)
UICornerMusic.Parent = MusicButton

-- 音乐按钮边框
local UIStrokeMusic = Instance.new("UIStroke")
UIStrokeMusic.Color = Color3.fromRGB(150, 100, 200)
UIStrokeMusic.Thickness = 1.5
UIStrokeMusic.Transparency = 0.7
UIStrokeMusic.Parent = MusicButton

-- 音乐按钮渐变
local MusicGradient = Instance.new("UIGradient")
MusicGradient.Rotation = 90
MusicGradient.Color = ColorSequence.new({
    ColorSequenceKeypoint.new(0, Color3.fromRGB(80, 60, 120)),
    ColorSequenceKeypoint.new(1, Color3.fromRGB(50, 30, 80))
})
MusicGradient.Parent = MusicButton

-- 音乐按钮悬停效果
MusicButton.MouseEnter:Connect(function()
    game:GetService("TweenService"):Create(
        MusicButton,
        TweenInfo.new(0.2),
        {BackgroundTransparency = 0.1, TextColor3 = Color3.fromRGB(255, 255, 255)}
    ):Play()
    game:GetService("TweenService"):Create(
        UIStrokeMusic,
        TweenInfo.new(0.2),
        {Transparency = 0.2}
    ):Play()
end)

MusicButton.MouseLeave:Connect(function()
    game:GetService("TweenService"):Create(
        MusicButton,
        TweenInfo.new(0.2),
        {BackgroundTransparency = 0.3, TextColor3 = Color3.fromRGB(200, 200, 255)}
    ):Play()
    game:GetService("TweenService"):Create(
        UIStrokeMusic,
        TweenInfo.new(0.2),
        {Transparency = 0.7}
    ):Play()
end)

-- 音乐控制变量
local musicPlaying = false
local sound

-- 按钮功能
Button1.MouseButton1Click:Connect(function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/dream77239/cut/refs/heads/main/cut"))()
end)

Button2.MouseButton1Click:Connect(function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/dream77239/idk/refs/heads/main/idk"))()
end)

Button3.MouseButton1Click:Connect(function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/dream77239/drwr-me/refs/heads/main/draw%20me"))()
end)

-- 音乐按钮功能
MusicButton.MouseButton1Click:Connect(function()
    if not musicPlaying then
        -- 创建声音
        sound = Instance.new("Sound")
        sound.SoundId = "rbxassetid://1838457617"
        sound.Looped = true
        sound.Parent = game:GetService("SoundService")
        sound:Play()
        MusicButton.Text = "停止音乐 (ID:1838457617)"
        musicPlaying = true
    else
        -- 停止声音
        if sound then
            sound:Stop()
            sound:Destroy()
        end
        MusicButton.Text = "播放音乐 (ID:1838457617)"
        musicPlaying = false
    end
end)

-- UI状态变量
local isMinimized = false

-- 关闭/收缩按钮功能
CloseButton.MouseButton1Click:Connect(function()
    isMinimized = not isMinimized
    
    if isMinimized then
        -- 收缩UI
        game:GetService("TweenService"):Create(
            MainFrame,
            TweenInfo.new(0.3),
            {Size = UDim2.new(0, 0, 0, 0), BackgroundTransparency = 1}
        ):Play()
        
        game:GetService("TweenService"):Create(
            Logo,
            TweenInfo.new(0.3),
            {ImageTransparency = 1}
        ):Play()
        
        game:GetService("TweenService"):Create(
            LogoGlow,
            TweenInfo.new(0.3),
            {ImageTransparency = 1}
        ):Play()
        
        wait(0.3)
        MainFrame.Visible = false
        MinimizedBall.Visible = true
        CloseButton.Image = "rbxassetid://6031094675"
        CloseButton.Rotation = 45
    else
        -- 展开UI
        MinimizedBall.Visible = false
        MainFrame.Visible = true
        
        game:GetService("TweenService"):Create(
            MainFrame,
            TweenInfo.new(0.3),
            {Size = UDim2.new(0, 400, 0, 320), BackgroundTransparency = 0.1}
        ):Play()
        
        game:GetService("TweenService"):Create(
            Logo,
            TweenInfo.new(0.3),
            {ImageTransparency = 0}
        ):Play()
        
        game:GetService("TweenService"):Create(
            LogoGlow,
            TweenInfo.new(0.3),
            {ImageTransparency = 0}
        ):Play()
        
        CloseButton.Image = "rbxassetid://6031094667"
        CloseButton.Rotation = 0
    end
end)

-- 小球点击功能
MinimizedBall.MouseButton1Click:Connect(function()
    isMinimized = false
    MinimizedBall.Visible = false
    MainFrame.Visible = true
    
    game:GetService("TweenService"):Create(
        MainFrame,
        TweenInfo.new(0.3),
        {Size = UDim2.new(0, 400, 0, 320), BackgroundTransparency = 0.1}
    ):Play()
    
    game:GetService("TweenService"):Create(
        Logo,
        TweenInfo.new(0.3),
        {ImageTransparency = 0}
    ):Play()
    
    game:GetService("TweenService"):Create(
        LogoGlow,
        TweenInfo.new(0.3),
        {ImageTransparency = 0}
    ):Play()
    
    CloseButton.Image = "rbxassetid://6031094667"
    CloseButton.Rotation = 0
end)

-- 拖拽功能
local UserInputService = game:GetService("UserInputService")
local dragging
local dragInput
local dragStart
local startPos

local function update(input)
    local delta = input.Position - dragStart
    MainFrame.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
    MinimizedBall.Position = UDim2.new(0, MainFrame.Position.X.Offset + MainFrame.Size.X.Offset - 60, 0, MainFrame.Position.Y.Offset)
    Logo.Position = UDim2.new(0, MainFrame.Position.X.Offset + MainFrame.Size.X.Offset/2 - 40, 0, MainFrame.Position.Y.Offset - 90)
    LogoGlow.Position = UDim2.new(0, MainFrame.Position.X.Offset + MainFrame.Size.X.Offset/2 - 60, 0, MainFrame.Position.Y.Offset - 110)
end

MainFrame.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
        dragging = true
        dragStart = input.Position
        startPos = MainFrame.Position
        
        input.Changed:Connect(function()
            if input.UserInputState == Enum.UserInputState.End then
                dragging = false
            end
        end)
    end
end)

MainFrame.InputChanged:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
        dragInput = input
    end
end)

UserInputService.InputChanged:Connect(function(input)
    if input == dragInput and dragging then
        update(input)
    end
end)

-- 小球拖拽功能
MinimizedBall.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
        dragging = true
        dragStart = input.Position
        startPos = MainFrame.Position
        
        input.Changed:Connect(function()
            if input.UserInputState == Enum.UserInputState.End then
                dragging = false
            end
        end)
    end
end)

MinimizedBall.InputChanged:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
        dragInput = input
    end
end)

-- 初始动画
MainFrame.Size = UDim2.new(0, 0, 0, 0)
MainFrame.Visible = true
game:GetService("TweenService"):Create(
    MainFrame,
    TweenInfo.new(0.5, Enum.EasingStyle.Back, Enum.EasingDirection.Out),
    {Size = UDim2.new(0, 400, 0, 320)}
):Play()
