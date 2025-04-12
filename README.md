-- Script simples de Auto Farm para Blox Fruits
-- ⚠️ Use com cuidado. Requer executores como Synapse X ou KRNL

-- Configurações
getgenv().AutoFarm = true
getgenv().AutoRaceV4 = true
getgenv().AutoFindIslands = true
getgenv().AutoGearMirage = true

-- Função para esperar personagem carregar
repeat wait() until game.Players.LocalPlayer and game.Players.LocalPlayer.Character

-- Função de Teleporte
function teleportTo(position)
    local player = game.Players.LocalPlayer
    if player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
        player.Character.HumanoidRootPart.CFrame = CFrame.new(position)
    end
end

-- Função de Auto Farm por level
spawn(function()
    while AutoFarm do
        local level = game.Players.LocalPlayer.Data.Level.Value
        -- Simples exemplo de farming até level 2450
        if level < 10 then
            -- Ir para ilha inicial e farmar Bandits
            teleportTo(Vector3.new(1050, 20, 1450)) -- Exemplo de posição
        elseif level < 50 then
            teleportTo(Vector3.new(1120, 20, 1550)) -- Nova área
        elseif level < 100 then
            teleportTo(Vector3.new(1200, 20, 1600)) -- Outra área
        else
            -- Pode adicionar mais ilhas aqui conforme o level sobe
            teleportTo(Vector3.new(2200, 25, 1200))
        end
        wait(10)
    end
end)

-- Função para tentar ativar Race V4
spawn(function()
    while AutoRaceV4 do
        -- Exemplo simples, você precisaria de executor avançado para interagir com UI e NPCs
        -- Teleporta para o templo do tempo (exemplo)
        teleportTo(Vector3.new(-5000, 300, -12000))
        wait(60) -- Espera para carregar
    end
end)

-- Função para encontrar ilhas
spawn(function()
    while AutoFindIslands do
        -- Isso requer checar o workspace por nomes de ilhas
        for _,v in pairs(workspace:GetChildren()) do
            if v:IsA("Model") and v.Name:find("Island") then
                print("Ilha encontrada:", v.Name)
            end
        end
        wait(30)
    end
end)

-- Função para pegar engrenagens da Ilha da Miragem
spawn(function()
    while AutoGearMirage do
        teleportTo(Vector3.new(58300, 500, 13900)) -- Mirage Island (posição de exemplo)
        -- Esperar tempo de spawn e interação com engrenagem
        wait(60)
    end
end)
