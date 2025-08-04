-- SCRIPT DEL SERVIDOR (colocar en ServerScriptService)
local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")

-- Este es el "walkie-talkie" que usará el jugador para hablarle al servidor.
local ReturnEvent = Instance.new("RemoteEvent")
ReturnEvent.Name = "ReturnBrainrotEvent"
ReturnEvent.Parent = ReplicatedStorage

local BRAINROT_NAMES = {
    "La Grande Combinasion", "La Vaca Saturno Saturnita", "Graipuss Medussi",
    "Los Tralaleritos", "Garama and Mandundung", "Chicleteira Bicicleteira",
    "Nuclearo Dinossauro", "Las Tralaleritas", "Las Combinasionas",
    "Tralalero Tralala", "Ondin din dun", "Girafa Celestre"
}

-- Función que se activa cuando el jugador toca un brainrot
local function onReturnRequest(player, brainrotModel)
    if not brainrotModel or not brainrotModel:IsA("Model") then return end

    local isBrainrot = false
    for _, brainrotName in ipairs(BRAINROT_NAMES) do
        if brainrotModel.Name == brainrotName then
            isBrainrot = true
            break
        end
    end

    if isBrainrot then
        local ownerValue = brainrotModel:FindFirstChild("Owner")
        
        if ownerValue and ownerValue:IsA("StringValue") then
            local ownerPlayer = Players:FindFirstChild(ownerValue.Value)

            if ownerPlayer and ownerPlayer.Backpack then
                local tool = Instance.new("Tool")
                tool.Name = brainrotModel.Name
                tool.Parent = ownerPlayer.Backpack
                
                if brainrotModel.PrimaryPart then
                    local handle = Instance.new("Part")
                    handle.Name = "Handle"
                    handle.Size = brainrotModel.PrimaryPart.Size
                    handle.CFrame = brainrotModel.PrimaryPart.CFrame
                    handle.Transparency = 1
                    handle.CanCollide = false
                    handle.Parent = tool
                    tool.Handle = handle
                end

                for _, child in ipairs(brainrotModel:GetChildren()) do
                    if child:IsA("BasePart") or child:IsA("MeshPart") or child:IsA("StringValue") then
                        child.Parent = tool
                    end
                end
                
                brainrotModel:Destroy()
                print("Brainrot '" .. tool.Name .. "' devuelto a '" .. ownerPlayer.Name .. "'.")
            end
        end
    end
end

ReturnEvent.OnServerEvent:Connect(onReturnRequest)

