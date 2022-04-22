--[[
PETERHOOK
BEST CHEAT EVER!!!

Unfortunately made by Property
This is the shittiest script I've ever made.
]]
local Peterhook = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local ImageLabel = Instance.new("ImageLabel")
local TextLabel = Instance.new("TextLabel")
local TextButton = Instance.new("TextButton")
local TextButton_2 = Instance.new("TextButton")
local TextButton_3 = Instance.new("TextButton")


Peterhook.Name = "Peterhook"
Peterhook.Parent = game.CoreGui
Peterhook.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

Frame.Parent = Peterhook
Frame.Active = true
Frame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Frame.BorderSizePixel = 0
Frame.Position = UDim2.new(0.04611497, 0, 0.0429447852, 0)
Frame.Size = UDim2.new(0, 523, 0, 334)
Frame.Draggable = true

ImageLabel.Parent = Frame
ImageLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
ImageLabel.BorderSizePixel = 0
ImageLabel.Size = UDim2.new(0, 523, 0, 334)
ImageLabel.Image = "http://www.roblox.com/asset/?id=5001010014"

TextLabel.Parent = Frame
TextLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
TextLabel.BackgroundTransparency = 1.000
TextLabel.BorderSizePixel = 0
TextLabel.Position = UDim2.new(0.0210325047, 0, 0.0239520967, 0)
TextLabel.Size = UDim2.new(0, 253, 0, 50)
TextLabel.Font = Enum.Font.Cartoon
TextLabel.Text = "PETERHOOK"
TextLabel.TextColor3 = Color3.fromRGB(98, 255, 0)
TextLabel.TextScaled = true
TextLabel.TextSize = 14.000
TextLabel.TextWrapped = true
TextLabel.TextXAlignment = Enum.TextXAlignment.Left

TextButton.Parent = Frame
TextButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
TextButton.BackgroundTransparency = 0.500
TextButton.BorderSizePixel = 0
TextButton.Position = UDim2.new(0.0210325047, 0, 0.215568855, 0)
TextButton.Size = UDim2.new(0, 306, 0, 52)
TextButton.Font = Enum.Font.Cartoon
TextButton.Text = "ANTICHEAT BYPASS"
TextButton.TextColor3 = Color3.fromRGB(255, 0, 4)
TextButton.TextScaled = true
TextButton.TextSize = 14.000
TextButton.TextWrapped = true

TextButton_2.Parent = Frame
TextButton_2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
TextButton_2.BackgroundTransparency = 0.500
TextButton_2.BorderSizePixel = 0
TextButton_2.Position = UDim2.new(0.0210325047, 0, 0.422155678, 0)
TextButton_2.Size = UDim2.new(0, 233, 0, 52)
TextButton_2.Font = Enum.Font.Cartoon
TextButton_2.Text = "MELEE AURA"
TextButton_2.TextColor3 = Color3.fromRGB(186, 48, 255)
TextButton_2.TextScaled = true
TextButton_2.TextSize = 14.000
TextButton_2.TextWrapped = true

TextButton_3.Parent = Frame
TextButton_3.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
TextButton_3.BackgroundTransparency = 0.500
TextButton_3.BorderSizePixel = 0
TextButton_3.Position = UDim2.new(0.0210325047, 0, 0.658682644, 0)
TextButton_3.Size = UDim2.new(0, 167, 0, 52)
TextButton_3.Font = Enum.Font.Cartoon
TextButton_3.Text = "SPEED"
TextButton_3.TextColor3 = Color3.fromRGB(84, 255, 230)
TextButton_3.TextScaled = true
TextButton_3.TextSize = 14.000
TextButton_3.TextWrapped = true

-- Scripts:

local function GQGY_fake_script() -- TextButton.LocalScript 
	local script = Instance.new('LocalScript', TextButton)

	script.Parent.MouseButton1Click:connect(function()
		local LocalPlayer = game.Players.LocalPlayer
		local oldNameCall
		oldNameCall = hookmetamethod(game,"__namecall",function(self,...)
			local args = {...}
			local method = getnamecallmethod()
			if not checkcaller() and getcallingscript().Name == "LocalClean" then -- localclean is retarded tbh (localclean causes those 1 sec lag spikes)
				return {}
			end
			if method == "FireServer" and self.Name == "RequestPlayerKick" then -- block humanoidcontrol requests for localplayer kick
				return "fortnite sussy balls :pensive:"
			end
			return oldNameCall(self,...)
		end)
		while game:GetService("RunService").RenderStepped:Wait() do
			if LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("CharacterControl") then -- not bothered to hook charactercontrol functions so just disable the script
				LocalPlayer.Character:FindFirstChild("CharacterControl").Disabled = true
			end
		end
	end)
end
coroutine.wrap(GQGY_fake_script)()
local function UYIA_fake_script() -- TextButton_2.LocalScript 
	local script = Instance.new('LocalScript', TextButton_2)

	script.Parent.MouseButton1Click:connect(function()
	local LocalPlayer = game.Players.LocalPlayer
		while wait(1/16) do 
			local s,e = pcall(function()
				local Character = LocalPlayer.Character
				local MeleePatch = ""
				for i,v in pairs(LocalPlayer.Character:GetChildren()) do
					if string.find(v.Name,"MeleeWeaponHandler") then
						MeleePatch = v.ToolName.value
					end
				end
				if MeleePatch ~= "" and LocalPlayer.Character then
					for i,v in pairs(game.Players:GetChildren()) do
						if v.Character and v ~= LocalPlayer and v.Team ~= LocalPlayer.Team then
							if (v.Character.Torso.Position - LocalPlayer.Character.Torso.Position).Magnitude < 30 then
								local args = {
									[1] = v.Character.Torso,
									[2] = v.Character.Torso.Position,
									[3] = Character[MeleePatch],
									[4] = "Melee"
								}
								game.ReplicatedStorage.Requests.RequestDamage:FireServer(unpack(args))
							end
						end
					end
				end
			end) if e then print("PETERHOOK FART ERROR: "..e) end
			end
	end)
end
coroutine.wrap(UYIA_fake_script)()
local function HGRE_fake_script() -- TextButton_3.LocalScript 
	local script = Instance.new('LocalScript', TextButton_3)

	script.Parent.MouseButton1Click:connect(function()
		while wait() do
			game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 70
		end
	end)
end
coroutine.wrap(HGRE_fake_script)()
