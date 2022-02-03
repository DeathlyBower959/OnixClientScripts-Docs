# Quick Start

## Install Scripts

Setup the directories needed for scripts to work with the client!

1. Press Win + R and paste: `explorer.exe %localappdata%\Packages\Microsoft.MinecraftUWP_8wekyb3d8bbwe\RoamingState\OnixClient`
2. Create a scripts folder in the current folder
3. Open Minecraft, and type `.lua reload`
4. Download a script that you would like ([https://github.com/OnixClient-Scripts/OnixClient\_Scripts](https://github.com/OnixClient-Scripts/OnixClient\_Scripts))

{% hint style="info" %}
Use `.lua reload after editing any files`
{% endhint %}

{% hint style="warning" %}
**Remember:** Make sure to save the files as `.lua` and not as `.txt or any other format.`
{% endhint %}

## Make your first script

This is a basic script, but it makes sure that you have correctly configured your scripts!

{% tabs %}
{% tab title="Lua" %}
```python
name = "Copy Coordinate"
description = "Copy coordinates at the press of a button!"



--[[
  Remember to use comments so others know certain functionality of the code!
--]]

Get_Player_Position_Key = 0x4F --or the 'O' key
Get_Selected_Block_Position_Key = 0x4A --or the 'J' key

client.settings.addKeybind("Get Player Position", "Get_Player_Position_Key")
client.settings.addKeybind("Get Block Selection", "Get_Selected_Block_Position_Key")

--script start

function keyboard(key, isDown)
    if (isDown == true) then
        if (key == Get_Player_Position_Key) then
            local x,y,z = player.position()
            setClipboard(x .. " " .. y .. " " .. z)
            client.notification("Your player coordinates are now in your clipboard!")
        else if (key == Get_Selected_Block_Position_Key) then
            if (player.facingBlock()) then
                local x,y,z = player.selectedPos()
                setClipboard(x .. " " .. y .. " " .. z)
                client.notification("Your selected coordinates are now in your clipboard!")
            else
                client.notification("You do not have a selected block.")
            end
            end
        end
    end
end
event.listen("KeyboardInput", keyboard)
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
**Remember:** `.lua reload`
{% endhint %}

