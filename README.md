local player = game.Players.LocalPlayer
local camera = game.Workspace.CurrentCamera
local highlightColor = Color3.fromRGB(255, 0, 0)  -- Cor do vermelho 

-- Função para desenhar o ESP
function createESP(target)
    local char = target.Character
    if not char or not char:FindFirstChild("Head") then return end

    local head = char.Head
    local box = Instance.new("BoxHandleAdornment")
    box.Adornee = head
    box.Size = Vector3.new(4, 4, 4)
    box.Color3 = highlightColor
    box.Transparency = 0.5
    box.ZIndex = 10
    box.Parent = game.CoreGui
end

-- Monitorar jogadores
game.Players.PlayerAdded:Connect(function(target)
    if target ~= player then
        createESP(target)
    end
end)
