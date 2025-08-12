local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local GuiService = game:GetService("GuiService")

-- 创建ScreenGui
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "ColorChangingText"
screenGui.ResetOnSpawn = false
screenGui.DisplayOrder = 999  -- 确保在最前面显示
screenGui.Parent = LocalPlayer:WaitForChild("PlayerGui")

-- 创建文本标签
local textLabel = Instance.new("TextLabel")
textLabel.Size = UDim2.new(1, 0, 1, 0)
textLabel.Position = UDim2.new(0, 0, 0, 0)
textLabel.BackgroundTransparency = 1
textLabel.Text = "🐦验证通过，ESP正在扫描全图🐦"
textLabel.Font = Enum.Font.SourceSansBold
textLabel.TextSize = 36
textLabel.TextColor3 = Color3.new(1, 1, 1)
textLabel.TextStrokeTransparency = 0.5
textLabel.TextStrokeColor3 = Color3.new(0, 0, 0)
textLabel.ZIndex = 10
textLabel.Parent = screenGui

-- 调整文本位置使其居中
textLabel.AnchorPoint = Vector2.new(0.5, 0.5)
textLabel.Position = UDim2.new(0.5, 0, 0.5, 0)

-- 颜色变化函数
local function changeColor()
    local time = 0
    local duration = 5 -- 5秒
    
    while time < duration do
        local hue = (tick() * 24) % 360
        textLabel.TextColor3 = Color3.fromHSV(hue/360, 1, 1)
        wait(0.05)
        time = time + 0.05
    end
    
    -- 5秒后移除
    screenGui:Destroy()
end

-- 启动颜色变化
coroutine.wrap(changeColor)()

-- ▼▼▼ 以下是第二个ESP脚本 ▼▼▼
-- 等待5秒脚本（适用于Delta注入器）
local waitTime = 5 -- 等待时间（秒）
local startTime = tick()

print("⏳ 脚本将在 "..waitTime.." 秒后开始执行...")

while tick() - startTime < waitTime do
    -- 每隔1秒打印一次剩余时间
    local remaining = math.floor(waitTime - (tick() - startTime))
    if remaining ~= lastRemaining then
        print("🕒 剩余时间: "..remaining.."秒")
        lastRemaining = remaining
    end
    wait(0.1)
end

print("✅ 等待结束，开始执行主脚本...")

-- 在这里拼接你的主脚本
-- 你的主脚本内容从这里开始...
loadstring(game:HttpGet("https://chen20110218.github.io/ESp2.3.2011",true))()
