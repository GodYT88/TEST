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
game:GetService'VirtualUser':CaptureController()
game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
end

loadstring(game:HttpGet("https://paste.gg/p/anonymous/6fddc46e6f734b6397817e6c1cde5738/files/5067e565bc17404a87909bdcfc721b2a/raw"))()

_G.Gate_Tween = false
_G.Method = "Behind"
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
