
_G.AntiAFKEnabled = true
local vu = game:GetService("VirtualUser")
local toolName;
game.Players.LocalPlayer.Idled:connect(
    function()
        if _G.AntiAFKEnabled then
            vu:Button2Down(Vector2.new(0, 0), workspace.CurrentCamera.CFrame)
            wait(1)
            vu:Button2Up(Vector2.new(0, 0), workspace.CurrentCamera.CFrame)
        end
    end
)

---------------------------------------------------------------------------------------------------------------------------------------- 


local openshit = Instance.new("ScreenGui")
local mainopen = Instance.new("TextButton")
local mainopens = Instance.new("UICorner")
local loki = Instance.new("ImageLabel")
local posto = Instance.new("UIStroke")

openshit.Name = "openshit"
openshit.Parent = game.CoreGui
openshit.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

local UICorner_11 = Instance.new("UICorner")
local UICorner_12 = Instance.new("UICorner")

local buttonframe = Instance.new("Frame")

local ImageButton_2 = Instance.new("ImageButton")

buttonframe.Parent = openshit
buttonframe.Name = "buttonframe"
buttonframe.BackgroundColor3 = Color3.fromRGB(0,0,0)
buttonframe.BorderColor3 = Color3.fromRGB(0, 0, 0)
buttonframe.BackgroundTransparency = 1.000
buttonframe.BorderSizePixel = 0
buttonframe.Position = UDim2.new(0.00790273491, 0, 0.233524337, 0)
buttonframe.Size = UDim2.new(0, 51, 0, 50)

UICorner_11.Parent = buttonframe
UICorner_12.Parent = ImageButton_2

ImageButton_2.Parent = buttonframe
ImageButton_2.BackgroundColor3 = Color3.fromRGB(86,255,255)
ImageButton_2.BorderColor3 = Color3.fromRGB(86,255,255)
ImageButton_2.BackgroundTransparency = 1.000
ImageButton_2.BorderSizePixel = 0
ImageButton_2.Position = UDim2.new(0.0242961459, 0, 0.0168576241, 0)
ImageButton_2.Size = UDim2.new(0, 49, 0, 48)
ImageButton_2.Image = "rbxassetid://16476263184"
ImageButton_2.MouseButton1Click:Connect(function()
    local screenGui = game.CoreGui:FindFirstChild("ScreenGui")
    if screenGui then
        screenGui.Enabled = not screenGui.Enabled
    end
end)

mainopens.Parent = mainopen
 
loki.Name = "loki"
loki.Parent = mainopen
loki.BackgroundColor3 = Color3.fromRGB(224,224,224)
loki.BackgroundTransparency = 1.000
loki.Position = UDim2.new(-0.0529999994, 0, -0.244000003, 0)
loki.Size = UDim2.new(0, 69, 0, 62)
loki.Image = "rbxassetid://16476263184"
 
posto.Name = "posto"
posto.Parent = mainopen
posto.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
posto.Color = Color3.fromRGB(224,224,224)
posto.LineJoinMode = Enum.LineJoinMode.Round
posto.Thickness = 1
posto.Transparency = 0
posto.Enabled = true
posto.Archivable = true

local UserInputService = game:GetService("UserInputService")
local TweenService = game:GetService("TweenService")

local function MakeDraggable(topbarobject, object)
    local Dragging = nil
    local DragInput = nil
    local DragStart = nil
    local StartPosition = nil

    local function Update(input)
        local Delta = input.Position - DragStart
        local pos = UDim2.new(StartPosition.X.Scale, StartPosition.X.Offset + Delta.X, StartPosition.Y.Scale, StartPosition.Y.Offset + Delta.Y)
        local Tween = TweenService:Create(object, TweenInfo.new(0.15), {
            Position = pos
        })
        Tween:Play()
    end

    topbarobject.InputBegan:Connect(
        function(input)
            if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
                Dragging = true
                DragStart = input.Position
                StartPosition = object.Position

                input.Changed:Connect(
                    function()
                        if input.UserInputState == Enum.UserInputState.End then
                            Dragging = false
                        end
                    end
                )
            end
        end
    )

    topbarobject.InputChanged:Connect(
        function(input)
            if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
                DragInput = input
            end
        end
    )

    UserInputService.InputChanged:Connect(
        function(input)
            if input == DragInput and Dragging then
                Update(input)
            end
        end
    )
end

MakeDraggable(buttonframe, openshit)

-- [Body Gyro]£
   spawn(function()
			while task.wait() do
				pcall(function()
			  if _G.FarmSelect or _G.AutoFBoss or _G.AutoFGEMV1 or  _G.Gate_Tween then
						if not game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip") then
							local Noclip = Instance.new("BodyVelocity")
							Noclip.Name = "BodyClip"
							Noclip.Parent = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart
							Noclip.MaxForce = Vector3.new(100000,100000,100000)
							Noclip.Velocity = Vector3.new(0,0,0)
						end
					else
						game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip"):Destroy()
					end
				end)
			end
   end)
	
	
--No CLip Auto Farm
spawn(function()
  pcall(function()
    game:GetService("RunService").Stepped:Connect(function()
      if _G.FarmSelect or _G.AutoFBoss or _G.AutoFGEMV1 or  _G.Gate_Tween then
      for i,v in pairs(game:GetService("Players").LocalPlayer.Character:GetDescendants()) do
      if v:IsA("BasePart") then
      v.CanCollide = false
      end
      end
      end
      end)
    end)
end)

        spawn(
            function()
                while wait(0.1) do
                    if _G.FarmSelect or _G.AutoFBoss or _G.AutoFGEMV1 or  _G.Gate_Tween then
                        pcall(
                            function()
                                local aa = game.Players.LocalPlayer.Character.HumanoidRootPart

                                if not aa:FindFirstChild("Haki") then
                                    local args = {
                                        [1] = "BusoHaki"
                                    }
                                    game:GetService("ReplicatedStorage").Remotes.SkillHolder:FireServer(unpack(args))
                                end
                            end
                        )
                    end
                end
            end
        )


spawn(function()
    while wait() do
        pcall(function()
            if AutoSkill then
                if Skillz then
                    game:service('VirtualInputManager'):SendKeyEvent(true, "Z", false, game)
                    wait(.1)
                    game:service('VirtualInputManager'):SendKeyEvent(false, "Z", false, game)
                end
                if Skillx then
                    game:service('VirtualInputManager'):SendKeyEvent(true, "X", false, game)
                    wait(.1)
                    game:service('VirtualInputManager'):SendKeyEvent(false, "X", false, game)
                end
                if Skillc then
                    game:service('VirtualInputManager'):SendKeyEvent(true, "C", false, game)
                    wait(.1)
                    game:service('VirtualInputManager'):SendKeyEvent(false, "C", false, game)
                end
                if Skillv then
                    game:service('VirtualInputManager'):SendKeyEvent(true, "V", false, game)
                    wait(.1)
                    game:service('VirtualInputManager'):SendKeyEvent(false, "V", false, game)
                end
                if Skillf then
                    game:service('VirtualInputManager'):SendKeyEvent(true, "F", false, game)
                    wait(.1)
                    game:service('VirtualInputManager'):SendKeyEvent(false, "F", false, game)
                end
            end
        end)
    end
end)


        MON = {
            "Bandit",
            "Bandit Leader",
            "Clown Pirate",
            "Marine",
            "Monkey",
            "Monkey King",
            "Bomb Man",
            "Sand Man",
            "Snow Bandit",
            "Snow Bandit Leader"
        }

        function MonA()
            if free == "Bandit" then
                MONName = "Bandit [LV.5]"
            elseif free == "Bandit Leader" then
                MONName = "Bandit Leader [LV.15]"
            elseif free == "Clown Pirate" then
                MONName = "Clown Pirate [LV.50]"
            elseif free == "Marine" then
                MONName = "Marine [LV.300]"
            elseif free == "Monkey" then
                MONName = "Monkey [LV.750]"
            elseif free == "Monkey King" then
                MONName = "Monkey King [LV.1000]"
            elseif free == "Bomb Man" then
                MONName = "Bomb Man [LV.1500]"
            elseif free == "Sand Man" then
                MONName = "Sand Man [LV.2000]"
            elseif free == "Snow Bandit" then
                MONName = "Snow Bandit [LV.1750]"
            elseif free == "Snow Bandit Leader" then
                MONName = "Snow Bandit Leader [LV.2350]"
            end
        end

        function QuestA()
            if free == "Bandit" then
                CFrameQuest =
                    CFrame.new(
                    -953.566528,
                    34.5999947,
                    -552.164612,
                    -0.0109250434,
                    -3.3378329e-09,
                    -0.999940336,
                    1.94075778e-09,
                    1,
                    -3.35923622e-09,
                    0.999940336,
                    -1.97734162e-09,
                    -0.0109250434
                )
            elseif free == "Bandit Leader" then
                CFrameQuest =
                    CFrame.new(
                    -1097.55042,
                    34.6000023,
                    -492.550354,
                    -0.0683717504,
                    2.67226739e-08,
                    0.997659922,
                    5.38579563e-08,
                    1,
                    -2.30943531e-08,
                    -0.997659922,
                    5.21529238e-08,
                    -0.0683717504
                )
            elseif free == "Clown Pirate" then
                CFrameQuest =
                    CFrame.new(
                    -71.5784531,
                    36.4347496,
                    50.7921715,
                    0.00707866857,
                    2.668971e-08,
                    0.999974966,
                    -5.85915032e-08,
                    1,
                    -2.62756199e-08,
                    -0.999974966,
                    -5.84040372e-08,
                    0.00707866857
                )
            elseif free == "Marine" then
                CFrameQuest =
                    CFrame.new(
                    848.661377,
                    35.5073013,
                    1264.83777,
                    -0.998497367,
                    5.36386899e-08,
                    0.0548002385,
                    5.90094018e-08,
                    1,
                    9.63871685e-08,
                    -0.0548002385,
                    9.94760612e-08,
                    -0.998497367
                )
            elseif free == "Monkey" then
                CFrameQuest =
                    CFrame.new(
                    771.192871,
                    42.3243141,
                    -1220.74805,
                    -0.996942639,
                    2.59707669e-08,
                    0.0781369284,
                    2.55865924e-08,
                    1,
                    -5.91784355e-09,
                    -0.0781369284,
                    -3.90049282e-09,
                    -0.996942639
                )
            elseif free == "Monkey King" then
                CFrameQuest =
                    CFrame.new(
                    727.094971,
                    42.2545357,
                    -1380.22131,
                    -0.0418852083,
                    2.64795439e-08,
                    0.999122441,
                    -2.36735005e-08,
                    1,
                    -2.74952416e-08,
                    -0.999122441,
                    -2.48043701e-08,
                    -0.0418852083
                )
            elseif free == "Snow Bandit" then
                CFrameQuest =
                    CFrame.new(
                    1507.57898,
                    102.05999,
                    -290.12558,
                    -0.998586833,
                    -8.202373e-09,
                    -0.0531440228,
                    -1.01186872e-08,
                    1,
                    3.57898209e-08,
                    0.0531440228,
                    3.62769903e-08,
                    -0.998586833
                )
            elseif free == "Bomb Man" or "Sand Man" or "Snow Bandit Leader" then
                CFrameQuest = nil
            end
        end

        function No()
            for i, v in ipairs(workspace.Lives:GetChildren()) do
                if not game:GetService("Players"):GetPlayerFromCharacter(v) then -- if not player then
                    local cleanedName = string.gsub(v.Name, "%d+$", "")
                    v.Name = tostring(cleanedName)
                end
            end

            workspace.Lives.ChildAdded:Connect(
                function(model)
                    task.wait(1)
                    if not game:GetService("Players"):GetPlayerFromCharacter(model) then -- if not player then
                        local cleanedName = string.gsub(model.Name, "%d+$", "")
                        model.Name = cleanedName
                    end
                end
            )
        end

        local Players =
            assert(
            assert(game, "game missing?"):FindService("Players") or game:GetService("Players"),
            "Players missing?"
        )
        local LocalPlayer = assert(Players.LocalPlayer, "LocalPlayer missing?")
        local replaces_str = {Players.LocalPlayer.Name}

        function TPCHEST()
            --[[pcall(
                function()
                    for i, v in pairs(game:GetService("Workspace").Chests:GetDescendants()) do
                        if v.ClassName == "ProximityPrompt" then
                            fireproximityprompt(v, 30)
                            TP(v.Parent.CFrame)
                        end
                    end
                end
            )]]
        end


        function TP(P)
         if game:GetService("Players").LocalPlayer.PlayerGui.LocalScript.Click then
            Distance = (P.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
            if Distance < 10 then
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = P
            elseif Distance > 50 then
                Speed = 500
            elseif Distance > 219 then
                Speed = 1000
            elseif Distance > 300 then
                Speed = 1500
            end
            game:GetService("TweenService"):Create(
                game:GetService("Players").LocalPlayer.Character.HumanoidRootPart,
                TweenInfo.new(Distance / Speed, Enum.EasingStyle.Linear),
                {CFrame = P}
            ):Play()
         end
        end
    

function click()
pcall(function()
	if game:GetService("Players").LocalPlayer.Character.Humanoid.Health >= 1 then
	game:GetService'VirtualUser':CaptureController()
	game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
 	game:GetService'VirtualUser':Button1Up(Vector2.new(1280, 672))
        end
end)
end

        spawn(
            function()
                while wait() do
                    pcall(
                        function()
                            if _G.AutoFBoss then
                                for _, v in pairs(game:GetService("Workspace").Lives:GetDescendants()) do
                                    if table.find(BossGem, v.Name) then
                                        if v.Humanoid.Health > 0 then
                                         if game:GetService("Players").LocalPlayer.PlayerGui.LocalScript.Click then
  
                                            repeat
                                                task.wait()

if _G.Method == "Behind" then
TP(v.HumanoidRootPart.CFrame * CFrame.new(0,0,_G.Distance) * CFrame.Angles(math.rad(0),0,0))
elseif _G.Method == "Front" then
TP(v.HumanoidRootPart.CFrame * CFrame.new(0,0,-_G.Distance) * CFrame.Angles(math.rad(0),0,-90))
elseif _G.Method == "Under" then
TP(v.HumanoidRootPart.CFrame * CFrame.new(0,-_G.Distance,0) * CFrame.Angles(math.rad(90),0,0))
elseif _G.Method == "Over" then
TP(v.HumanoidRootPart.CFrame * CFrame.new(0,_G.Distance,0) * CFrame.Angles(math.rad(-90),0,0))
elseif _G.Method == "XYLO-Custom" then
spawn(function()
TP(v.HumanoidRootPart.CFrame * CFrame.new(5,4,_G.Distance) * CFrame.Angles(math.rad(-45),0,0))
task.wait(0.1)
TP(v.HumanoidRootPart.CFrame * CFrame.new(5,4,_G.Distance) * CFrame.Angles(math.rad(-45),0,0))
end)
end
click()
TPCHEST()
                                            until _G.AutoFBoss == false or v.Humanoid.Health <= 0
                                        end
                                    end
                                end
                                end
                           end
                        end
                    )
                end
            end
        )

        _G.Distance = 5

        local Sekboosss =
            CFrame.new(
            2085.1936,
            118.110451,
            -2335.99731,
            -0.976698041,
            -1.59721765e-08,
            0.214618161,
            -5.54776136e-09,
            1,
            4.9174254e-08,
            -0.214618161,
            4.68377479e-08,
            -0.976698041
        )




        No()

        spawn(
            function()
                while wait() do
                    pcall(
                        function()
                            if _G.AutoAttackBossOrb then
                                EqOrb()
                                TP(Sekboosss)
                                ClickProximityPrompt()
                                TPCHEST()
                                for _, v in pairs(game:GetService("Workspace").Lives:GetChildren()) do
                                    if table.find(BossWorld, v.Name) then
                                        if v.Humanoid.Health > 0 then
                                            repeat
                                                task.wait()

if _G.Method == "Behind" then
TP(v.HumanoidRootPart.CFrame * CFrame.new(0,0,_G.Distance) * CFrame.Angles(math.rad(0),0,0))
elseif _G.Method == "Front" then
TP(v.HumanoidRootPart.CFrame * CFrame.new(0,0,-_G.Distance) * CFrame.Angles(math.rad(0),0,-90))
elseif _G.Method == "Under" then
TP(v.HumanoidRootPart.CFrame * CFrame.new(0,-_G.Distance,0) * CFrame.Angles(math.rad(90),0,0))
elseif _G.Method == "Over" then
TP(v.HumanoidRootPart.CFrame * CFrame.new(0,_G.Distance,0) * CFrame.Angles(math.rad(-90),0,0))
end
                                              
                                 click()       
                                                TPCHEST()
                                            until _G.AutoAttackBossOrb == false or v.Humanoid.Health <= 0
                                        end
                                    end
                                end
                            end
                        end
                    )
                end
            end
        )

        function tools()
            spawn(
                function()
                    _G.tools = true
                    while _G.tools do
                        wait()
                        pcall(
                            function()
                                local args = {
                                    [1] = toolsname
                                }

                                game:GetService("ReplicatedStorage").Remotes.EquipItem:FireServer(unpack(args))
                                wait(1)
                                if game.Players.LocalPlayer.Backpack:FindFirstChild(tostring(toolsname)) then
                                    _G.tools = false -- Stop the EquipTool process
                                end
                            end
                        )
                    end
                end
            )
        end


        function EqOrb()
            spawn(
                function()
                    local toolName = toolsname -- Replace with the name of your tool
                    local tool = game.Players.LocalPlayer.Backpack[toolName]

                    if tool then
                        game.Players.LocalPlayer.Character.Humanoid:EquipTool(tool)
                    end
                end
            )
        end

        spawn(
            function()
                while wait() do
                    pcall(
                        function()
                            if _G.Farn then
                                MonA()
                                for _, v in pairs(game:GetService("Workspace").Lives:GetChildren()) do
                                    if v.Humanoid.DisplayName == MONName and v.Humanoid.Health > 0 then
                                        v.HumanoidRootPart.Size = Vector3.new(20, 20, 20)
                                        v.HumanoidRootPart.Transparency = 0.9
                                        v.Humanoid.WalkSpeed = 0
                                        v.Humanoid:ChangeState(14)
                                        v.HumanoidRootPart.CanCollide = false
                                        v.Head.CanCollide = false
                                        if v.Humanoid:FindFirstChild("Animator") then
                                            v.Humanoid.Animator:Destroy()
                                        end
                                        repeat
                                            task.wait()
if _G.Method == "Behind" then
TP(v.HumanoidRootPart.CFrame * CFrame.new(0,0,_G.Distance) * CFrame.Angles(math.rad(0),0,0))
elseif _G.Method == "Front" then
TP(v.HumanoidRootPart.CFrame * CFrame.new(0,0,-_G.Distance) * CFrame.Angles(math.rad(0),0,-90))
elseif _G.Method == "Under" then
TP(v.HumanoidRootPart.CFrame * CFrame.new(0,-_G.Distance,0) * CFrame.Angles(math.rad(90),0,0))
elseif _G.Method == "Over" then
TP(v.HumanoidRootPart.CFrame * CFrame.new(0,_G.Distance,0) * CFrame.Angles(math.rad(-90),0,0))
end
                                      click()
                                        until _G.Farn == false or v.Humanoid.Health <= 0
                                    end
                                end
                            end
                        end
                    )
                end
            end
        )

        spawn(
            function()
                while wait() do
                    pcall(
                        function()
                            if _G.Gate_Tween then
                                for _, v in pairs(game:GetService("Workspace").Lives:GetChildren()) do
                                    if table.find(GateMob, v.Name) then
                                        if v.Humanoid.Health > 0 then
                                            repeat
                                                task.wait()
if _G.Method == "Behind" then
TP(v.HumanoidRootPart.CFrame * CFrame.new(0,0,_G.Distance) * CFrame.Angles(math.rad(0),0,0))
elseif _G.Method == "Front" then
TP(v.HumanoidRootPart.CFrame * CFrame.new(0,0,-_G.Distance) * CFrame.Angles(math.rad(0),0,-90))
elseif _G.Method == "Under" then
TP(v.HumanoidRootPart.CFrame * CFrame.new(0,-_G.Distance,0) * CFrame.Angles(math.rad(90),0,0))
elseif _G.Method == "Over" then
TP(v.HumanoidRootPart.CFrame * CFrame.new(0,_G.Distance,0) * CFrame.Angles(math.rad(-90),0,0))
end
click()
                                            until _G.Gate_Tween == false or v.Humanoid.Health <= 0
                                        end
                                    end
                                end
                            end
                        end
                    )
                end
            end)

        spawn(
            function()
                while wait() do
                    pcall(
                        function()
                            if _G.Gate_Tween then
                                for _, Gate in pairs(workspace.World.Portal:GetChildren()) do
                                    --local CommonGate = workspace.World.Portal.Common
                                    TP(Gate.CFrame)
                                end
                            end
                        end
                    )
                end
            end
        )

        function ClickProximityPrompt()
            for _, v in pairs(game:GetService("Workspace"):GetDescendants()) do
                if v.ClassName == "ProximityPrompt" then
                    fireproximityprompt(v, 30)
                end
            end
        end

        local Players =
            assert(
            assert(game, "game missing?"):FindService("Players") or game:GetService("Players"),
            "Players missing?"
        )
        local LocalPlayer = assert(Players.LocalPlayer, "LocalPlayer missing?")
        local replaces_str = {Players.LocalPlayer.Name}
print(Players.LocalPlayer.Name)
        spawn(
            function()
                while wait() do
                    pcall(
                        function()
                            if  _G.Gate_Tween then
                                 for i,v in pairs(workspace.World.Portal:GetChildren()) do
                                if not game.workspace.World.Portal[v.Name].Script.Dungeonn[Players.LocalPlayer.Name] then
                                 ClickProximityPrompt()
                                end
                                end
                                          end
                           end)
                   end
          end)  

spawn(
    function()
        while wait() do
            pcall(
                function()
                    Date = os.date("%d" .. " " .. "%B" .. " " .. "%Y")
                end
            )
        end
    end
)

       
        local Fluent =
            loadstring(
            game:HttpGet(
                "https://paste.gg/p/anonymous/6fddc46e6f734b6397817e6c1cde5738/files/5067e565bc17404a87909bdcfc721b2a/raw"
            )
        )()
        local SaveManager =
            loadstring(
            game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/SaveManager.lua")
        )()
        local InterfaceManager =
            loadstring(
            game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/InterfaceManager.lua")
        )()
       


        local Window =
            Fluent:CreateWindow(
            {
                Title = "Kurumi | Hub" .. "Executor " .. tostring(identifyexecutor()) .. " [ " .. Date .. " ] ",
                SubTitle = "",
                TabWidth = 160,
                Size = UDim2.fromOffset(560, 350),
                Acrylic = false, -- The blur may be detectable, setting this to false disables blur entirely
                Theme = "Rose",
                MinimizeKey = Enum.KeyCode.End -- Used when theres no MinimizeKeybind
            }
        )

local Options = Fluent.Options

        local Gate = {
            GateGod = Window:AddTab({Title = "Gate", Icon = "Kurumi"})
        }

        local Solo = Gate.GateGod:AddSection("Auto Gate")

        Solo:AddParagraph(
            {
                Title = "Auto Kill In Gate /Gate Support Legend And Common",
            }
        )

        Solo:AddToggle(
            "Gate",
            {
                Title = "Auto Tween To Gate And Auto Kill Mob In Gate",
                Default = false,
                Callback = function(GATEGGG)
                    _G.Gate_Tween = GATEGGG
                end
            }
        )

loadstring(game:HttpGetAsync("https://raw.githubusercontent.com/atomic86447/List/main/ListOnline.lua"))()

        local Tabs = {
            Farm = Window:AddTab({Title = "Farm Settings", Icon = "Kurumi"})
        }

local FarmSettings = Tabs.Farm:AddSection("Farm Settings")

FarmSettings:AddDropdown(
            "Method",
            {
                Title = "Select Method",
                Values = {"Behind", "Front", "Over", "Under", "XYLO-Custom"},
                Multi = false,
                Default = "เลือก-Select",
                Callback = function(Value)
                    _G.Method = Value
                end
            }
        )
       
        FarmSettings:AddParagraph(
            {
                Title = "if Equip Not to switch",
                Content = "ถ้ามันไม่ถือให้ กดสลับ"
            }
        )

Wapon = {}
for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do
        table.insert(Wapon,v.Name)
end

local MobDP = FarmSettings:AddDropdown("Weapon", {
                Title = "Select Weapon",
                Values = Wapon,
                Multi = false,
                Default = false,
                Callback = function(a)
                _G.Weapon = a
		toolName = a
                  end 
            })
spawn(function()
            while wait(1) do
             if _G.FarmSelect or _G.AutoFBoss or _G.AutoFGEMV1 or  _G.Gate_Tween then 
                pcall(function()
                 if game:GetService("Players").LocalPlayer.PlayerGui.LocalScript.Click then
                    game.Players.LocalPlayer.Character.Humanoid:EquipTool(game:GetService("Players").LocalPlayer.Backpack[_G.Weapon])
                    wait(1)
                    end
                end)
            end
            end
       end)
        FarmSettings:AddButton({
               Title = "Refresh Weapon",
               Callback = function(v)
                   local Wapon = {}
                   for _,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
                       if not table.find(Wapon, v.Name) then
                           table.insert(Wapon, v.Name)
                        end
                    end
        
                   MobDP:SetValues(Wapon)
               end
           })

        FarmSettings:AddButton(
            {
                Title = "Boost FPS",
                Callback = function()
                    local decalsyeeted = true
                    local g = game
                    local w = g.Workspace
                    local l = g.Lighting
                    local t = w.Terrain
                    sethiddenproperty(l, "Technology", 2)
                    sethiddenproperty(t, "Decoration", false)
                    t.WaterWaveSize = 0
                    t.WaterWaveSpeed = 0
                    t.WaterReflectance = 0
                    t.WaterTransparency = 0
                    l.GlobalShadows = 0
                    l.FogEnd = 9e9
                    l.Brightness = 0
                    settings().Rendering.QualityLevel = "Level01"
                    for i, v in pairs(w:GetDescendants()) do
                        if v:IsA("BasePart") and not v:IsA("MeshPart") then
                            v.Material = "Plastic"
                            v.Reflectance = 0
                        elseif (v:IsA("Decal") or v:IsA("Texture")) and decalsyeeted then
                            v.Transparency = 1
                        elseif v:IsA("ParticleEmitter") or v:IsA("Trail") then
                            v.Lifetime = NumberRange.new(0)
                        elseif v:IsA("Explosion") then
                            v.BlastPressure = 1
                            v.BlastRadius = 1
                        elseif v:IsA("Fire") or v:IsA("SpotLight") or v:IsA("Smoke") or v:IsA("Sparkles") then
                            v.Enabled = false
                        elseif v:IsA("MeshPart") and decalsyeeted then
                            v.Material = "Plastic"
                            v.Reflectance = 0
                            v.TextureID = 10385902758728957
                        elseif v:IsA("SpecialMesh") and decalsyeeted then
                            v.TextureId = 0
                        elseif v:IsA("ShirtGraphic") and decalsyeeted then
                            v.Graphic = 0
                        elseif (v:IsA("Shirt") or v:IsA("Pants")) and decalsyeeted then
                            v[v.ClassName .. "Template"] = 0
                        end
                    end
                    for i = 1, #l:GetChildren() do
                        e = l:GetChildren()[i]
                        if
                            e:IsA("BlurEffect") or e:IsA("SunRaysEffect") or e:IsA("ColorCorrectionEffect") or
                                e:IsA("BloomEffect") or
                                e:IsA("DepthOfFieldEffect")
                         then
                            e.Enabled = false
                        end
                    end
                    w.DescendantAdded:Connect(
                        function(v)
                            wait()
                            --prevent errors and shit
                            if v:IsA("BasePart") and not v:IsA("MeshPart") then
                                v.Material = "Plastic"
                                v.Reflectance = 0
                            elseif v:IsA("Decal") or v:IsA("Texture") and decalsyeeted then
                                v.Transparency = 1
                            elseif v:IsA("ParticleEmitter") or v:IsA("Trail") then
                                v.Lifetime = NumberRange.new(0)
                            elseif v:IsA("Explosion") then
                                v.BlastPressure = 1
                                v.BlastRadius = 1
                            elseif v:IsA("Fire") or v:IsA("SpotLight") or v:IsA("Smoke") or v:IsA("Sparkles") then
                                v.Enabled = false
                            elseif v:IsA("MeshPart") and decalsyeeted then
                                v.Material = "Plastic"
                                v.Reflectance = 0
                                v.TextureID = 10385902758728957
                            elseif v:IsA("SpecialMesh") and decalsyeeted then
                                v.TextureId = 0
                            elseif v:IsA("ShirtGraphic") and decalsyeeted then
                                v.ShirtGraphic = 0
                            elseif (v:IsA("Shirt") or v:IsA("Pants")) and decalsyeeted then
                                v[v.ClassName .. "Template"] = 0
                            end
                        end
                    )
                end
            }
        )

        FarmSettings:AddInput(
            "Input",
            {
                Title = "Distance",
                Default = 5,
                Placeholder = "Insert Distance",
                Numeric = true, -- Only allows numbers
                Finished = false, -- Only calls callback when you press enter
                Callback = function(Text)
                    _G.Distance = Text
                end
            }
        )

FarmSettings:AddToggle(
            "enablefarm",
            {
                Title = "AutoSkill",
                Default = false,
                Callback = function(AutoSkil)
                 AutoSkill = AutoSkil
                    Skillz = AutoSkil
                    Skillx = AutoSkil
                    Skillc = AutoSkil
                    Skillv = AutoSkil
                    Skillf = AutoSkil
                    
                end
            
            }
        )

        FarmSettings:AddToggle(
            "enablefarm",
            {
                Title = "WhiteScreen",
                Default = false,
                Callback = function(value)
                    _G.WhiteScreen = value
                    if _G.WhiteScreen == true then
                        game:GetService("RunService"):Set3dRenderingEnabled(false)
                    elseif _G.WhiteScreen == false then
                        game:GetService("RunService"):Set3dRenderingEnabled(true)
                    end
                end
            }
        )

        local BossSek = {
            AutoKillBossSek = Window:AddTab({Title = "Auto Sek BOSS", Icon = "Kurumi"})
        }

        local AutoKillBossSekVPaid = BossSek.AutoKillBossSek:AddSection("Auto Sek BOSS")

        local OrbSekk =
            AutoKillBossSekVPaid:AddDropdown(
            "Boss Orb",
            {
                Title = "Select Orb Boss",
                Values = OrbSekkBossOnline,
                Multi = false,
                Default = "เลือก-Select",
                Callback = function(text)
                    toolsname = text
                end
            }
        )

        AutoKillBossSekVPaid:AddToggle(
            "Boss",
            {
                Title = "Auto Spawn Boss + Auto Kill Boss",
                Default = false,
                Callback = function(v)
                    _G.AutoAttackBossOrb = v
                end
            }
        )

        AutoKillBossSekVPaid:AddToggle(
            "Boss",
            {
                Title = "Auto Take Orb out of your bag",
                Default = false,
                Callback = function(value)
                    _G.tools = value
                    if value then
                        tools()
                        _G.tools = true
                    else
                        _G.tools = false
                    end
                end
            }
        )

        AutoKillBossSekVPaid:AddToggle(
            "Boss",
            {
                Title = "Auto Use Holy Grail [ Mr. Tong held it.. ]",
                Default = false,
                Callback = function(value)
                    _G.Holy = value
                end
            }
        )

        spawn(
            function()
                while wait() do
                    pcall(
                        function()
                            if _G.Holy then
                                local args = {
                                    [1] = "Holy Grail"
                                }

                                game:GetService("ReplicatedStorage").Remotes.UseItemFromClient:FireServer(unpack(args))
                                game:GetService "VirtualUser":CaptureController()
                                game:GetService "VirtualUser":Button1Down(Vector2.new(590, 354))
                            end
                        end
                    )
                end
            end
        )

        local FullFarm = {
            FullFarmTap = Window:AddTab({Title = "Farm", Icon = "Kurumi"})
        }

        local FullyFarmTap = FullFarm.FullFarmTap:AddSection("Farm")

        FullyFarmTap:AddDropdown(
            "Mob",
            {
                Title = "Select Mob",
                Values = MON,
                Multi = false,
                Default = 1,
                Callback = function(ZELECT)
                    free = ZELECT
                end
            }
        )

        FullyFarmTap:AddToggle(
            "enablefarm",
            {
                Title = "Auto Farm",
                Default = false,
                Callback = function(t)
                    _G.Farn = t
                end
            }
        )

        FullyFarmTap:AddToggle(
            "enablefarm",
            {
                Title = "Auto Quest",
                Default = false,
                Callback = function(QuestFully1)
                    _G.AutoQuest = QuestFully1
                end
            }
        )
        spawn(
            function()
                while wait() do
                    pcall(
                        function()
                            if _G.AutoQuest then
                                QuestA()
                                if not game.Players.LocalPlayer.PlayerGui:FindFirstChild("QuestUI") then
                                    repeat
                                        task.wait()
                                        TP(CFrameQuest)
                                    until not _G.AutoQuest or
                                        game.Players.LocalPlayer.PlayerGui:FindFirstChild("QuestUI")
                                end
                            end
                        end
                    )
                end
            end
        )

        spawn(
            function()
                while wait() do
                    pcall(
                        function()
                            if _G.AutoQuest then
                                for i, v in pairs(game:GetService("Workspace"):GetDescendants()) do
                                    if v.Name == "ProximityPrompt" then
                                        fireproximityprompt(v, 30)
                                    end
                                end
                            end
                        end
                    )
                end
            end
        )

        FullyFarmTap:AddToggle(
            "enablefarm",
            {
                Title = "Auto Farm Boss + Gem",
                Default = false,
                Callback = function(GEMV1)
                    _G.AutoFBoss = GEMV1
                end
            }
        )

        local Npc = {
            NpcShop = Window:AddTab({Title = "Shop", Icon = "Kurumi"})
        }

        local NpcShopTP = Npc.NpcShop:AddSection("shop")

        local FruitSSS =
            NpcShopTP:AddDropdown(
            "Select Fruit",
            {
                Title = "Select Gruit",
                Values = FruitList,
                Multi = false,
                Default = "เลือก",
                Callback = function(v)
                    _G.FruitSelect = v
                end
            }
        )

        NpcShopTP:AddToggle(
            "Auto Random Fruit Select",
            {
                Title = "Auto Random Fruit Select",
                Default = false,
                Callback = function(FSE)
                    _G.FruitRD = FSE
                end
            }
        )

        NpcShopTP:AddToggle(
            "Auto Random Fruit No Select",
            {
                Title = "Auto Random",
                Default = false,
                Callback = function(S)
                    _G.FruitNOSEe = S
                end
            }
        )

        local Options = Fluent.Options
        function Nofty()
            Fluent:Notify(
                {
                    Title = "Fluent",
                    Content = "You Got Fruit Select",
                    Duration = 8
                }
            )
        end

        local Fruitteen =
            CFrame.new(
            -741.048889,
            43.4787788,
            -1933.82019,
            -0.0251465552,
            7.8026531e-08,
            0.999683797,
            -1.09866749e-09,
            1,
            -7.80788483e-08,
            -0.999683797,
            -3.06173398e-09,
            -0.0251465552
        )

        spawn(
            function()
                while wait() do
                    pcall(
                        function()
                            if _G.FruitRD then
                                for i, v in pairs(game:GetService("Workspace").Shop:GetDescendants()) do
                                    if v.ClassName == "ProximityPrompt" then
                                        fireproximityprompt(v, 30)
                                        TP(Fruitteen)
                                        if game.Players.LocalPlayer.Backpack:FindFirstChild(tostring(_G.FruitSelect)) then
                                            break
                                        end
                                    end
                                end
                            end
                        end
                    )
                end
            end
        )

        spawn(
            function()
                while wait() do
                    if _G.FruitRD then
                        if game.Players.LocalPlayer.Backpack:FindFirstChild(tostring(_G.FruitSelect)) then
                            wait(1)
                            Nofty()
                        end
                    end
                end
            end
        )

        spawn(
            function()
                while wait() do
                    pcall(
                        function()
                            if _G.FruitNOSEe then
                                for i, v in pairs(game:GetService("Workspace").Shop:GetDescendants()) do
                                    if v.ClassName == "ProximityPrompt" then
                                        fireproximityprompt(v, 30)
                                        TP(Fruitteen)
                                    end
                                end
                            end
                        end
                    )
                end
            end
        )

        local NPCC = {
            NPCTLP = Window:AddTab({Title = "Teleport", Icon = "Kurumi"}),
            Settings = Window:AddTab({Title = "Settings", Icon = "settings"})
        }

        local NPCTELEPORT = NPCC.NPCTLP:AddSection("Teleport NPC ")

        NPCTELEPORT:AddButton(
            {
                Title = "[Katana] [2500$]",
                Callback = function()
                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame =
                        CFrame.new(
                        -909.817078,
                        35.2999916,
                        -517.520386,
                        -0.997258246,
                        -5.08231457e-09,
                        0.0739996061,
                        -5.64554181e-09,
                        1,
                        -7.40204875e-09,
                        -0.0739996061,
                        -7.79952192e-09,
                        -0.997258246
                    )
                end
            }
        )

        NPCTELEPORT:AddButton(
            {
                Title = "[Yoru] [5000000$]",
                Callback = function()
                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame =
                        CFrame.new(
                        -1853.85852,
                        69.9719696,
                        32.3987617,
                        -0.0491525866,
                        -1.44003263e-08,
                        0.998791277,
                        -3.93964825e-08,
                        1,
                        1.24789707e-08,
                        -0.998791277,
                        -3.87354895e-08,
                        -0.0491525866
                    )
                end
            }
        )

        NPCTELEPORT:AddButton(
            {
                Title = "[Sukuna] [Require : 5 Sukuna Finger] [2500 Gem]",
                Callback = function()
                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame =
                        CFrame.new(
                        -917.713013,
                        34.5999947,
                        -488.171783,
                        0.999844313,
                        -2.79001942e-08,
                        -0.0176440775,
                        2.8142022e-08,
                        1,
                        1.34576252e-08,
                        0.0176440775,
                        -1.39520706e-08,
                        0.999844313
                    )
                end
            }
        )

        NPCTELEPORT:AddButton(
            {
                Title = "[Executioner] [Require : ???] [Disabled]",
                Callback = function()
                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame =
                        CFrame.new(
                        1658.28516,
                        102.659988,
                        -97.4339905,
                        0.39779678,
                        6.67110953e-08,
                        0.917473555,
                        -8.14363865e-09,
                        1,
                        -6.91808353e-08,
                        -0.917473555,
                        2.00483399e-08,
                        0.39779678
                    )
                end
            }
        )

        NPCTELEPORT:AddButton(
            {
                Title = "[Random Demon Fruit] [100 Gem]",
                Callback = function()
                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame =
                        CFrame.new(
                        -744.417419,
                        43.4787788,
                        -1936.01074,
                        0.99731791,
                        2.50135539e-08,
                        -0.0731918216,
                        -2.87462889e-08,
                        1,
                        -4.99459212e-08,
                        0.0731918216,
                        5.19159542e-08,
                        0.99731791
                    )
                end
            }
        )

        NPCTELEPORT:AddButton(
            {
                Title = "[Random Demon Fruit] [500000 Beli]",
                Callback = function()
                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame =
                        CFrame.new(
                        787.530762,
                        35.5073013,
                        1200.37122,
                        0.999804795,
                        -3.53292684e-08,
                        0.0197579358,
                        3.5835928e-08,
                        1,
                        -2.5289447e-08,
                        -0.0197579358,
                        2.59925539e-08,
                        0.999804795
                    )
                end
            }
        )

        NPCTELEPORT:AddButton(
            {
                Title = "[Gojo (Eye Patch) ] [Require : Infinity Orb] [3500 Gem]",
                Callback = function()
                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame =
                        CFrame.new(
                        1526.62134,
                        136.759964,
                        -257.611664,
                        0.050806988,
                        -8.10261902e-09,
                        0.998708487,
                        -2.63210076e-08,
                        1,
                        9.45211731e-09,
                        -0.998708487,
                        -2.6767248e-08,
                        0.050806988
                    )
                end
            }
        )

        NPCTELEPORT:AddButton(
            {
                Title = "[Cid's Sword] [Require : 5 Shadow Orb] [15000 Gem]",
                Callback = function()
                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame =
                        CFrame.new(
                        -2086.48389,
                        77.8514175,
                        655.046692,
                        0.999925077,
                        -3.57938346e-09,
                        0.0122415517,
                        3.236857e-09,
                        1,
                        2.80004535e-08,
                        -0.0122415517,
                        -2.79587322e-08,
                        0.999925077
                    )
                end
            }
        )

        NPCTELEPORT:AddButton(
            {
                Title = "[Remove Demon Fruit from Inventory] [Except : Secret & Mythical]",
                Callback = function()
                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame =
                        CFrame.new(
                        -678.306702,
                        40.3787766,
                        -1881.7594,
                        1,
                        -3.30142953e-08,
                        2.01401108e-14,
                        3.30142953e-08,
                        1,
                        9.71047385e-08,
                        -2.33459543e-14,
                        -9.71047385e-08,
                        1
                    )
                end
            }
        )

        NPCTELEPORT:AddButton(
            {
                Title = "[Kashimo's Pole V1] [50000000$]",
                Callback = function()
                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame =
                        CFrame.new(
                        838.588745,
                        42.4595222,
                        -1516.1405,
                        1,
                        3.96085653e-08,
                        8.85604493e-07,
                        -3.96084801e-08,
                        1,
                        -9.72064171e-08,
                        -8.85604493e-07,
                        9.72063816e-08,
                        1
                    )
                end
            }
        )

        NPCTELEPORT:AddButton(
            {
                Title = "[Kashimo's PoleV2 [Curse]] [Require :  Kashimo's Pole & 10 Lightning Orb] [15000 Gem]",
                Callback = function()
                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame =
                        CFrame.new(
                        998.657349,
                        35.5072975,
                        1237.68372,
                        -7.60766952e-08,
                        -4.58059475e-08,
                        -1,
                        9.41029032e-09,
                        1,
                        -4.5805951e-08,
                        1,
                        -9.41029388e-09,
                        -7.60766952e-08
                    )
                end
            }
        )

        NPCTELEPORT:AddButton(
            {
                Title = "[Itadori] [Require : 1 Sukuna Finger] [7500 Gem]",
                Callback = function()
                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame =
                        CFrame.new(
                        1834.22058,
                        57.2104073,
                        -2461.83496,
                        -0.847525597,
                        9.20146661e-08,
                        -0.530754507,
                        1.22204483e-07,
                        1,
                        -2.17742162e-08,
                        0.530754507,
                        -8.3314788e-08,
                        -0.847525597
                    )
                end
            }
        )

        NPCTELEPORT:AddButton(
            {
                Title = "[Gon] [Require : Gon's Fishing bait] [2500 Gem]",
                Callback = function()
                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame =
                        CFrame.new(
                        460.52655,
                        38.3999062,
                        -3006.6814,
                        -0.00754104555,
                        1.56928088e-08,
                        0.999971569,
                        -4.06405078e-08,
                        1,
                        -1.59997349e-08,
                        -0.999971569,
                        -4.07600069e-08,
                        -0.00754104555
                    )
                end
            }
        )

        NPCTELEPORT:AddButton(
            {
                Title = "[GojoV2 [Unleashed] ] [Require : Limitless] [5000 Gem]",
                Callback = function()
                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame =
                        CFrame.new(
                        -2448.97192,
                        64.2299652,
                        -1163.28821,
                        0.986545622,
                        -1.96925534e-08,
                        0.163486078,
                        9.2132002e-10,
                        1,
                        1.14894355e-07,
                        -0.163486078,
                        -1.13197906e-07,
                        0.986545622
                    )
                end
            }
        )

        NPCTELEPORT:AddButton(
            {
                Title = "[Uraume] [Require : 5 Cursed Ice Shard] [5000 Gem]",
                Callback = function()
                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame =
                        CFrame.new(
                        1933.35132,
                        111.110405,
                        -2177.22241,
                        -0.0343346596,
                        -6.64154527e-08,
                        -0.999410391,
                        -2.09004813e-08,
                        1,
                        -6.57366002e-08,
                        0.999410391,
                        1.86311144e-08,
                        -0.0343346596
                    )
                end
            }
        )

        NPCTELEPORT:AddButton(
            {
                Title = "[Sukuna [Half Power]] [Require : King of Curse's Soul] [5000  Gem]",
                Callback = function()
                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame =
                        CFrame.new(
                        -2460.72266,
                        55.483223,
                        -1446.37256,
                        -0.0169456564,
                        -1.44014569e-08,
                        -0.999856412,
                        -8.8613703e-08,
                        1,
                        -1.29016922e-08,
                        0.999856412,
                        8.83823503e-08,
                        -0.0169456564
                    )
                end
            }
        )

        -- Addons:
        -- SaveManager (Allows you to have a configuration system)
        -- InterfaceManager (Allows you to have a interface managment system)

        -- Hand the library over to our managers
SaveManager:SetLibrary(Fluent)
InterfaceManager:SetLibrary(Fluent)

-- Ignore keys that are used by ThemeManager.
-- (we dont want configs to save themes, do we?)
SaveManager:IgnoreThemeSettings()

-- You can add indexes of elements the save manager should ignore
SaveManager:SetIgnoreIndexes({})

-- use case for doing it this way:
-- a script hub could have themes in a global folder
-- and game configs in a separate folder per game
InterfaceManager:SetFolder("Kurumi Hub")
SaveManager:SetFolder("Kurumi Hub/specific-game")

InterfaceManager:BuildInterfaceSection(NPCC.Settings)
SaveManager:BuildConfigSection(NPCC.Settings)
Window:SelectTab(1)
SaveManager:LoadAutoloadConfig()
--[[
    else
        game.Players.LocalPlayer:Kick("Invalid Key! Please Rejoin And Try Again.")
    end
   ]]

        --.Vip Log Player
    --    loadstring(game:HttpGet("https://raw.githubusercontent.com/atomic86447/CheckKey/main/CheckKeyVSecret.lua"))()
----------------------------------------------------------------------------------------------------------------------------------------
--[[else
    print("Player Closed The GUI.")
end]]


