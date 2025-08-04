-- SCRIPT DEL CLIENTE (colocar en StarterPlayerScripts)
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local ReturnEvent = ReplicatedStorage:WaitForChild("ReturnBrainrotEvent")

local BRAINROT_NAMES = {
    "La Grande Combinasion", "La Vaca Saturno Saturnita", "Graipuss Medussi",
    "Los Tralaleritos", "Garama and Mandundung", "Chicleteira Bicicleteira",
    "Nuclearo Dinossauro", "Las Tralaleritas", "Las Combinasionas",
    "Tralalero Tralala", "Ondin din dun", "Girafa Celestre"
}

-- Función que se ejecuta cuando algo toca a un brainrot
local function onTouched(partTouched)
    local brainrotModel = partTouched.Parent
    if not brainrotModel then return end

    local isBrainrot = false
    for _, brainrotName in ipairs(BRAINROT_NAMES) do
        if brainrotModel.Name == brainrotName then
            isBrainrot = true
            break
        end
    end

    if isBrainrot then
        -- Le habla al servidor para que devuelva este brainrot
        ReturnEvent:FireServer(brainrotModel)
    end
end

-- Recorre todos los brainrots existentes y conecta su evento de toque
for _, object in ipairs(workspace:GetChildren()) do
    local isBrainrot = false
    for _, brainrotName in ipairs(BRAINROT_NAMES) do
        if object.Name == brainrotName then
            isBrainrot = true
            break
        end
    end

    if isBrainrot and object:IsA("Model") and object.PrimaryPart then
        object.PrimaryPart.Touched:Connect(onTouched)
    end
end

-- Asegura que los nuevos brainrots que aparezcan también tengan el evento de toque
workspace.ChildAdded:Connect(function(child)
    if child:IsA("Model") and child.PrimaryPart then
        local isBrainrot = false
        for _, brainrotName in ipairs(BRAINROT_NAMES) do
            if child.Name == brainrotName then
                isBrainrot = true
                break
            end
        end

        if isBrainrot then
            child.PrimaryPart.Touched:Connect(onTouched)
        end
    end
end)
