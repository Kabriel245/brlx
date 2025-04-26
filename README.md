-- MODO DEUS ATIVADO: Script fictício para o Blox Fruits
-- Vamos pegar todas as Bandanas e dominar o mundo!

repeat wait() until game:IsLoaded()
wait(2)

local player = game.Players.LocalPlayer
local char = player.Character or player.CharacterAdded:Wait()
local hrp = char:WaitForChild("HumanoidRootPart")

-- 🌀 TELEPORT: Teleporta para as localizações das Bandanas
local bandanaLocations = {
    Vector3.new(1100, 5, 1400), -- Exemplo de coordenadas
    Vector3.new(1500, 5, 1800), -- Outra localização fictícia
    Vector3.new(2000, 5, 2300), -- Mais uma
}

-- Função para teleportar para uma das Bandanas
function teleportToBandana(location)
    hrp.CFrame = CFrame.new(location)
end

-- 💥 HAKI INFINITO (simulado)
if char:FindFirstChild("Haki") then
    char.Haki.Enabled = true
else
    local haki = Instance.new("BoolValue")
    haki.Name = "Haki"
    haki.Parent = char
    haki.Value = true
end
print("HAKI DO REI ATIVADO 😤")

-- 🍇 FRUTAS INFINITAS
local function spawnFruit(name)
    local fruit = Instance.new("Tool")
    fruit.Name = name
    fruit.Parent = player.Backpack
    print("Fruta adicionada: " .. name)
end

-- EXEMPLO: Spawnar 3 frutas
spawnFruit("Dragon Fruit")
spawnFruit("Leopard Fruit")
spawnFruit("Dough Fruit")

-- 💨 VELOCIDADE INFINITA
char:WaitForChild("Humanoid").WalkSpeed = 200
char.Humanoid.JumpPower = 150
print("Modo Flash Ativado ⚡")

-- 💀 AUTO-KILL FICTÍCIO: Mata inimigos e bosses
function autoKill()
    -- Mata inimigos comuns
    for _, v in pairs(workspace.Enemies:GetChildren()) do
        if v:FindFirstChild("Humanoid") then
            v.Humanoid.Health = 0
            print("Inimigo eliminado: " .. v.Name)
        end
    end

    -- Mata todos os bosses
    for _, v in pairs(workspace.Bosses:GetChildren()) do
        if v:FindFirstChild("Humanoid") then
            v.Humanoid.Health = 0
            print("Boss eliminado: " .. v.Name)
        end
    end
end

-- Função para pegar Bandana: Coleta a Bandana quando ela é tocada
function collectBandana(bandana)
    -- Verifica se a Bandana está tocando o personagem
    local touched = false
    bandana.Touched:Connect(function(hit)
        if not touched then
            local player = game.Players:GetPlayerFromCharacter(hit.Parent)
            if player then
                touched = true
                bandana:Destroy() -- "Destrói" a Bandana ao coletá-la
                print(player.Name .. " coletou uma Bandana!")
            end
        end
    end)
end

-- Função para realizar a missão de pegar as Bandanas
function autoMissionBandanas()
    for _, location in pairs(bandanaLocations) do
        teleportToBandana(location)  -- Teleporta para cada local da Bandana
        wait(2) -- Espera 2 segundos para garantir que o personagem chegou
        -- Vamos tentar pegar a Bandana aqui (supondo que a Bandana esteja lá)
        local bandana = workspace:FindFirstChild("Bandana") -- Aqui, 'Bandana' é o nome do objeto
        if bandana then
            collectBandana(bandana)
        else
            print("Bandana não encontrada no local!")
        end
    end
end

-- Chama a função de auto-kill constantemente
while true do
    autoKill() -- Mata inimigos e bosses
    autoMissionBandanas() -- Realiza a missão de pegar as Bandanas
    wait(5) -- Espera 5 segundos antes de repetir o processo
end

-- 🧠 CONTROLE TOTAL: Modo de Deus ativado
print("🌌 TUDO ATIVADO — Blox Fruits modo Deus 🐉")
# brlx
