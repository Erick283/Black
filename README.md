
-- Script Local ou ServerScript dependendo do uso
-- Esse exemplo é ServerScript (coloque em ServerScriptService)

game.Players.PlayerAdded:Connect(function(player)
    player.CharacterAdded:Connect(function(char)
        -- Espera o HumanoidRootPart
        local hrp = char:WaitForChild("HumanoidRootPart")

        -- Cria a hitbox
        local hitbox = Instance.new("Part")
        hitbox.Size = Vector3.new(6, 6, 6) -- tamanho da hitbox
        hitbox.Transparency = 0.7           -- deixa meio visível (0 = sólido / 1 = invisível)
        hitbox.Color = Color3.fromRGB(200, 0, 200) -- roxo
        hitbox.Anchored = false
        hitbox.CanCollide = false
        hitbox.Name = "CustomHitbox"
        hitbox.Parent = char

        -- Cola a hitbox no HRP, mas deslocada para cima
        local weld = Instance.new("WeldConstraint")
        weld.Part0 = hrp
        weld.Part1 = hitbox
        weld.Parent = hrp

        -- Posição da hitbox (acima da cabeça)
        hitbox.CFrame = hrp.CFrame * CFrame.new(0, 10, 0) -- 10 studs acima
    end)
end)
