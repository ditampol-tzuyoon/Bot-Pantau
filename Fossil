function ohdsay(logger)
    if getBot().status == "Online" then
        statzBot = ":green_circle:"
    else
        statzBot = ":red_circle:"
    end

    if isWeared(3934) then
        Chisel = "~ "..itemInfo(3934).name.." (x"..findItem(3934)..") **[WEARED]**"
    else
        Chisel = "~ "..itemInfo(3934).name.." (x"..findItem(3934)..") **[NOT WEARED]**"
    end

    if isWeared(3932) then
        Hammer = "~ "..itemInfo(3932).name.." (x"..findItem(3932)..") **[WEARED]**"
    else
        Hammer = "~ "..itemInfo(3932).name.." (x"..findItem(3932)..") **[NOT WEARED]**"
    end

    Poli = "~ "..itemInfo(4134).name.." (x"..ScanPoli..")"
    Batu = "~ "..itemInfo(10).name.." (x"..findItem(10)..")"
    Brush = "~ "..itemInfo(4132).name.." (x"..findItem(4132)..")"

    WorldSkrg = (getBot().world):upper()
    if Sensor then
        Muncul = false
        for _, v in pairs(World) do
            if v:upper() == WorldSkrg then
                Muncul = true
            end
        end
        if WorldStorage:upper() == WorldSkrg then
            Muncul = true
        end
        if Muncul then
            WorldSkrg = WorldSkrg:gsub(string.sub(WorldSkrg, 1, string.len(Teks_Sensor)), Teks_Sensor)
        end
    end

    URLWeb = hookURL.."/messages/"..HookID

    local script = [[

    $w = "]]..URLWeb..[["

    [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
    $interface = Get-NetConnectionProfile
    $ip = Get-NetIPAddress -InterfaceAlias $interface.InterfaceAlias -AddressFamily IPv4 | ForEach-Object IPAddress
    $CompObject = Get-WmiObject -Class WIN32_OperatingSystem
    $Rams = ((($CompObject.TotalVisibleMemorySize - $CompObject.FreePhysicalMemory)*100)/ $CompObject.TotalVisibleMemorySize)
    $Ram = [Math]::Floor($Rams)
    $CPUs = (Get-WmiObject Win32_Processor | Measure-Object -Property LoadPercentage -Average | Select Average).Average
    $CPU = [Math]::Floor($CPUs)

    [System.Collections.ArrayList]$embedArray = @()
    $descriptions = ']].. logger ..[['
    $color       = ']]..math.random(1000000,9999999)..[['


    $footerObject = [PSCustomObject]@{
        text = 'Panen Fossil by Ohdear#2320'
    }

    $authorObject = [PSCustomObject]@{
        name = "Fossil (]]..#ListPembeli..[[ Buyers) || Author : Ohdear#2320"
        url = "https://discord.gg/TjVwdgma74"
        icon_url = "https://assets.pikiran-rakyat.com/crop/0x0:0x0/x/photo/2022/05/16/3828930929.jpg"
    }

    $fieldArray = @(

        @{
            name = "]]..emot_bot..[[ Bot Name"
            value = "]]..getBot().name..[["
            inline = "true"
        }
        @{
            name = "]]..emot_world..[[ Current World"
            value = "]]..WorldSkrg..[["
            inline = "true"
        }
        @{
            name = "]]..statzBot..[[ Bot Status"
            value = "]]..getBot().status..[["
            inline = "true"
        }

        @{
            name = "]]..emot_bahan..[[ Bahan"
            value = "]]..Brush..[[`n]]..Batu..[["
            inline = "true"
        }
        @{
            name = "]]..emot_tas..[[ Inventory Slot"
            value = "]]..getInventoryData().count..[[/]]..getInventoryData().slot..[["
            inline = "true"
        }
        @{
            name = "]]..emot_alat..[[ Alat"
            value = "]]..Hammer..[[`n]]..Chisel..[["
            inline = "true"
        }

        @{
            name = "]]..emot_world..[[ World Fossil"
            value = "]]..ShowWorld..[["
            inline = "true"
        }
        @{
            name = "]]..emot_world..[[ World Storage"
            value = "]]..Poli..[["
            inline = "true"
        }
    )

    $embedObject = [PSCustomObject]@{
        description = $descriptions
        color       = $color
        footer      = $footerObject
        author      = $authorObject
        fields      = $fieldArray
    }

    $embedArray.Add($embedObject) | Out-Null

    $Body = [PSCustomObject]@{

        embeds = $embedArray

        'username' = ']]..getBot().name..[[ | OD2320'

    }

    Invoke-RestMethod -Uri $w -Body ($Body | ConvertTo-Json -Depth 4) -Method Patch -ContentType 'application/json'
    ]]

    local pipe = io.popen("powershell -command -", "w")
    pipe:write(script)
    pipe:close()
end
