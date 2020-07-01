---
title: VSPerfASPNetCmd | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- profiling tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: f9e9f895-57bb-41e8-8bd1-cdaa738ec220
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b6ddadc15a5e0d53535b82d87aadd31fec65adaf
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/24/2020
ms.locfileid: "85330476"
---
# <a name="vsperfaspnetcmd"></a>VSPerfASPNetCmd
La herramienta de línea de comandos **VSPerfASPNetCmd.exe** le permite generar perfiles de sitios web de ASP.NET sin necesidad de establecer variables de entorno ni reiniciar el equipo. Use **VSPerfASPNetCmd.exe** en lugar de [VSPerfCmd](../profiling/vsperfcmd.md) cuando genere perfiles de sitios web de ASP.NET y no necesite la funcionalidad adicional proporcionada por **VSPerCmd**. Para más información sobre [VSPerfASPNetCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md), vea **Generación rápida de perfiles de sitio web con VSPerfASPNETCmd**. **VSPerfASPNetCmd** es la herramienta de línea de comandos preferida cuando se usa el generador de perfiles independiente para generar perfiles de un sitio web de ASP.NET.

## <a name="syntax"></a>Sintaxis
 **vsperfaspnetcmd** [/*Opciones*] *Sitio web*

## <a name="options"></a>Opciones

|Opción|Descripción|
|------------|-----------------|
|**/Sample** o **/s**|Genera perfiles de sitios web utilizando el método de muestreo. **/Sample** es el método predeterminado. /Sample no se puede utilizar con **/Trace**.|
|**/Trace** o **/t**|Genera perfiles de sitios web utilizando el método de instrumentación. /Trace no se puede utilizar con **/Sample**.|
|**/Memory**[ **:** `Type`]o **/m**[ **:** {**a**&#124;**l**}]|Genera perfiles de asignación de memoria y opcionalmente de duraciones de objetos (recopilación de elementos no utilizados). **/Memory** se puede utilizar con el método de muestreo o de instrumentación.<br /><br /> El elemento *Type* puede ser uno de los siguientes:<br /><br /> -   **allocation** (o **a**) recopila únicamente datos de asignación de memoria.<br />-   **lifetime** (o **l**) recopila datos de asignación de memoria y de duración de objetos.<br /><br /> El valor predeterminado de `Type` es **allocation**.|
|**/Tip** o **/i**|Agrega información detallada de solicitudes de ASP.NET y llamadas de ADO.NET a los datos de generación de perfiles. **/Tip** se puede utilizar con el método de muestreo o de instrumentación y con la opción **/Memory**.|
|**/Output:** `File` o **/o:** `File`|Especifica la ruta de acceso y el nombre del archivo de datos de generación de perfiles (.*vsp*).|
|**/NoWait** o **/n**|Devuelve el símbolo del sistema inmediatamente para que los comandos adicionales se puedan utilizar en la ventana de símbolo del sistema. Para desactivar la generación de perfiles, debe escribir **VSPerfASPNETCmd /Shutdown** en una línea de comandos independiente.|
|**/PackSymbols**[:{**on**&#124;**off**}or   **/p**[:{**on**&#124;**off**}|Inserta símbolos (nombres de función y parámetro, etc.) en el archivo de datos de generación de perfiles (.*vsp*).|
|**/Shutdown:** `Website` o **/d:** `Website`|Desactiva la generación de perfiles. Se utiliza como única opción en una línea de comandos después de utilizar la opción **/NoWait** para empezar a generar perfiles o si el generador de perfiles finaliza inesperadamente. Especifique la misma dirección URL que utilizó en el comando **VSPerfASPNETCmd** original.|
|`Website`|La dirección URL del sitio web cuyo perfil se va a generar.|

## <a name="see-also"></a>Vea también
- [Generación rápida de perfiles de sitio web con VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)
- [Generación de perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
