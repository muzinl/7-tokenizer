# 7-tokenizer

# Client Side

local SecurityToken = nil

Citizen.CreateThread(function()
    while SecurityToken == nil do
        Citizen.Wait(1500)
        TriggerServerEvent("seven:ask:for:token", GetCurrentResourceName())
    end
end)

RegisterNetEvent('seven:get:token', function(resourceName, token)
    if resourceName == GetCurrentResourceName() then
        SecurityToken = token
    end
end)

TriggerServerEvent('moneytrigger', money, SecurityToken)

# Server Side

RegisterNetEvent('moneytrigger', function(money, token)
    local src = source
    local money = math.random(999, 999)

    if not exports['7-tokenizer']:checkToken(src, GetCurrentResourceName(), token) then
        Hier je ban code
        return
    end
    print(money)
end)
