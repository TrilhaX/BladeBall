warn('[TEMPEST HUB] Loading Bypass')
wait(1)
warn('[TEMPEST HUB] Loading Ui')
wait(1)
local repo = 'https://raw.githubusercontent.com/violin-suzutsuki/LinoriaLib/main/'

local Library = loadstring(game:HttpGet(repo .. 'Library.lua'))()
local ThemeManager = loadstring(game:HttpGet(repo .. 'addons/ThemeManager.lua'))()
local SaveManager = loadstring(game:HttpGet(repo .. 'addons/SaveManager.lua'))()

local Window = Library:CreateWindow({
    Title = 'Tempest Hub | Blade Ball',
    Center = true,
    AutoShow = true,
    TabPadding = 8,
    MenuFadeTime = 0.2
})

Library:Notify('Loading Blade Ball Script', 5)

warn('[TEMPEST HUB] Loading Functions')
wait(1)

function autoparry()
    while getgenv().autoparry == true do
        local Debug = false -- Set this to true if you want my debug output.
        local ReplicatedStorage = game:GetService("ReplicatedStorage")
        local Players = game:GetService("Players")
        
        local Player = Players.LocalPlayer or Players.PlayerAdded:Wait()
        local Remotes = ReplicatedStorage:WaitForChild("Remotes", 9e9) -- A second argument in waitforchild what could it mean?
        local Balls = workspace:WaitForChild("Balls", 9e9)
        
        -- Functions
        
        local function print(...) -- Debug print.
            if Debug then
                warn(...)
            end
        end
        
        local function VerifyBall(Ball) -- Returns nil if the ball isn't a valid projectile; true if it's the right ball.
            if typeof(Ball) == "Instance" and Ball:IsA("BasePart") and Ball:IsDescendantOf(Balls) and Ball:GetAttribute("realBall") == true then
                return true
            end
        end
        
        local function IsTarget() -- Returns true if we are the current target.
            return (Player.Character and Player.Character:FindFirstChild("Highlight"))
        end
        
        local function Parry() -- Parries.
            Remotes:WaitForChild("ParryButtonPress"):Fire()
        end
        
        -- The actual code
        
        Balls.ChildAdded:Connect(function(Ball)
            if not VerifyBall(Ball) then
                return
            end
            
            print(`Ball Spawned: {Ball}`)
            
            local OldPosition = Ball.Position
            local OldTick = tick()
            
            Ball:GetPropertyChangedSignal("Position"):Connect(function()
                if IsTarget() then -- No need to do the math if we're not being attacked.
                    local Distance = (Ball.Position - workspace.CurrentCamera.Focus.Position).Magnitude
                    local Velocity = (OldPosition - Ball.Position).Magnitude -- Fix for .Velocity not working. Yes I got the lowest possible grade in accuplacer math.
                    
                    print(`Distance: {Distance}\nVelocity: {Velocity}\nTime: {Distance / Velocity}`)
                
                    if (Distance / Velocity) <= 10 then -- Sorry for the magic number. This just works. No, you don't get a slider for this because it's 2am.
                        Parry()
                    end
                end
                
                if (tick() - OldTick >= 1/60) then -- Don't want it to update too quickly because my velocity implementation is aids. Yes, I tried Ball.Velocity. No, it didn't work.
                    OldTick = tick()
                    OldPosition = Ball.Position
                end
            end)
        end)
        wait()
    end
end

function automaxhability()
    while getgenv().automaxhability == true do
    game:GetService("Players").LocalPlayer.Upgrades.Dash.Value = 2
    game:GetService("Players").LocalPlayer.Upgrades.Forcefield.Value = 2
    game:GetService("Players").LocalPlayer.Upgrades.Freeze.Value = 2
    game:GetService("Players").LocalPlayer.Upgrades.Infinity.Value = 2
    game:GetService("Players").LocalPlayer.Upgrades.Invisibility.Value = 2
    game:GetService("Players").LocalPlayer.Upgrades["Phase Bypass"].Value = 2
    game:GetService("Players").LocalPlayer.Upgrades.Platform.Value = 2
    game:GetService("Players").LocalPlayer.Upgrades.Pull.Value = 2
    game:GetService("Players").LocalPlayer.Upgrades["Raging Deflection"].Value = 2
    game:GetService("Players").LocalPlayer.Upgrades.Reaper.Value = 2
    game:GetService("Players").LocalPlayer.Upgrades["Shadow Step"].Value = 2
    game:GetService("Players").LocalPlayer.Upgrades["Super Jump"].Value = 2
    game:GetService("Players").LocalPlayer.Upgrades.Swap.Value = 2
    game:GetService("Players").LocalPlayer.Upgrades.Telekinesis.Value = 2
    game:GetService("Players").LocalPlayer.Upgrades["Thunder Dash"].Value = 2
    game:GetService("Players").LocalPlayer.Upgrades.Waypoint.Value = 2
    game:GetService("Players").LocalPlayer.Upgrades["Wind Cloak"].Value = 2
    wait(1)
    end
end

function SetWalkSpeed(Value)
    local walkSpeed = Value
    
    local UIS = game:GetService("UserInputService")
    local RS = game:GetService("RunService")
    local W, A, S, D
    local xVelo, yVelo
    
    while true do
        wait()
        local HRP = game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
        local C = game.Workspace.CurrentCamera
        local LV = C.CFrame.LookVector

        for i, v in pairs(UIS:GetKeysPressed()) do
            if v.KeyCode == Enum.KeyCode.W then
                W = true
            end
            if v.KeyCode == Enum.KeyCode.A then
                A = true
            end
            if v.KeyCode == Enum.KeyCode.S then
                S = true
            end
            if v.KeyCode == Enum.KeyCode.D then
                D = true
            end
        end

        if W == true and S == true then
            yVelo = false
            W, S = nil, nil
        end

        if A == true and D == true then
            xVelo = false
            A, D = nil, nil
        end

        if yVelo ~= false then
            if W == true then
                if xVelo ~= false then
                    if A == true then
                        local LeftLV = (C.CFrame * CFrame.Angles(0, math.rad(45), 0)).LookVector
                        HRP.Velocity = Vector3.new((LeftLV.X * walkSpeed), HRP.Velocity.Y, (LeftLV.Z * walkSpeed))
                        W, A = nil, nil
                    else
                        if D == true then
                            local RightLV = (C.CFrame * CFrame.Angles(0, math.rad(-45), 0)).LookVector
                            HRP.Velocity = Vector3.new((RightLV.X * walkSpeed), HRP.Velocity.Y, (RightLV.Z * walkSpeed))
                            W, D = nil, nil
                        end
                    end
                end
            else
                if S == true then
                    if xVelo ~= false then
                        if A == true then
                            local LeftLV = (C.CFrame * CFrame.Angles(0, math.rad(135), 0)).LookVector
                            HRP.Velocity = Vector3.new((LeftLV.X * walkSpeed), HRP.Velocity.Y, (LeftLV.Z * walkSpeed))
                            S, A = nil, nil
                        else
                            if D == true then
                                local RightLV = (C.CFrame * CFrame.Angles(0, math.rad(-135), 0)).LookVector
                                HRP.Velocity = Vector3.new((RightLV.X * walkSpeed), HRP.Velocity.Y, (RightLV.Z * walkSpeed))
                                S, D = nil, nil
                            end
                        end
                    end
                end
            end
        end

        if W == true then
            HRP.Velocity = Vector3.new((LV.X * walkSpeed), HRP.Velocity.Y, (LV.Z * walkSpeed))
        end
        if S == true then
            HRP.Velocity = Vector3.new(-(LV.X * walkSpeed), HRP.Velocity.Y, -(LV.Z * walkSpeed))
        end
        if A == true then
            local LeftLV = (C.CFrame * CFrame.Angles(0, math.rad(90), 0)).LookVector
            HRP.Velocity = Vector3.new((LeftLV.X * walkSpeed), HRP.Velocity.Y, (LeftLV.Z * walkSpeed))
        end
        if D == true then
            local RightLV = (C.CFrame * CFrame.Angles(0, math.rad(-90), 0)).LookVector
            HRP.Velocity = Vector3.new((RightLV.X * walkSpeed), HRP.Velocity.Y, (RightLV.Z * walkSpeed))
        end

        xVelo, yVelo, W, A, S, D = nil, nil, nil, nil, nil, nil
        wait()
    end
end

warn('[TEMPEST HUB] Checking Functions')
wait(1)

local Tabs = {
    Main = Window:AddTab('Main'),
}

local LeftGroupBox = Tabs.Main:AddLeftGroupbox('Player')

LeftGroupBox:AddSlider('Walkspeed', {
    Text = 'Walkspeed',
    Default = 16,
    Min = 16,
    Max = 100,
    Rounding = 1,
    Compact = false,
    Callback = function(Value)
        SetWalkSpeed(Value)
    end
})

local LeftGroupBox = Tabs.Main:AddLeftGroupbox('Farm')

LeftGroupBox:AddToggle('Auto Parry', {
    Text = 'Auto Parry',
    Default = false,
    Tooltip = 'Auto Parry',
    Callback = function(Value)
        getgenv().autoparry = Value
        autoparry()
    end
})

LeftGroupBox:AddToggle('Auto Max Hability', {
    Text = 'Auto Max Hability',
    Default = false,
    Tooltip = 'Auto Max Hability',
    Callback = function(Value)
        getgenv().automaxhability = Value
        automaxhability()
    end
})



local FrameTimer = tick()
local FrameCounter = 0
local FPS = 60

local WatermarkConnection
WatermarkConnection = game:GetService('RunService').RenderStepped:Connect(function()
    FrameCounter = FrameCounter + 1

    if (tick() - FrameTimer) >= 1 then
        FPS = FrameCounter
        FrameTimer = tick()
        FrameCounter = 0
    end

    Library:SetWatermark(('Tempest Hub | %s fps | %s ms'):format(
        math.floor(FPS),
        math.floor(game:GetService('Stats').Network.ServerStatsItem['Data Ping']:GetValue())
    ))
end)

local TabsUI = {
    ['UI Settings'] = Window:AddTab('UI Settings'),
}

Library:OnUnload(function()
    WatermarkConnection:Disconnect()
    print('Unloaded!')
    Library.Unloaded = true
end)

-- UI Settings
local MenuGroup = TabsUI['UI Settings']:AddLeftGroupbox('Menu')


MenuGroup:AddButton('Unload', function() Library:Unload() end)
MenuGroup:AddLabel('Menu bind'):AddKeyPicker('MenuKeybind', { Default = 'End', NoUI = true, Text = 'Menu keybind' })

-- Define a tabela 'Options'
Library.ToggleKeybind = Options.MenuKeybind

ThemeManager:SetLibrary(Library)
SaveManager:SetLibrary(Library)

ThemeManager:SetFolder('Tempest Hub')
SaveManager:SetFolder('Tempest Hub/Blade Ball')

SaveManager:BuildConfigSection(TabsUI['UI Settings'])

ThemeManager:ApplyToTab(TabsUI['UI Settings'])

SaveManager:LoadAutoloadConfig()

for i,v in pairs(getconnections(game.Players.LocalPlayer.Idled)) do
    v:Disable()
end
warn('[TEMPEST HUB] Loaded')
