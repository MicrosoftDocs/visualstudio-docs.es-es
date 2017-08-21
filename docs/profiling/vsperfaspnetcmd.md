---
title: VSPerfASPNetCmd | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: f9e9f895-57bb-41e8-8bd1-cdaa738ec220
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 223750aef8d997c6ae017f49ea0a9522bdba72bc
ms.openlocfilehash: ab57983a9dec6ce00e9edef4027b2a23f47d2ae1
ms.contentlocale: es-es
ms.lasthandoff: 08/10/2017

---
# <a name="vsperfaspnetcmd"></a>VSPerfASPNetCmd
La herramienta de línea de comandos **VSPerfASPNetCmd.exe** le permite generar perfiles de sitios web de ASP.NET sin necesidad de establecer variables de entorno ni reiniciar el equipo. Use **VSPerfASPNetCmd.exe** en lugar de [VSPerfCmd](../profiling/vsperfcmd.md) cuando genere perfiles de sitios web de ASP.NET y no necesite la funcionalidad adicional proporcionada por **VSPerCmd**. Para obtener más información sobre [VSPerfASPNetCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md), consulte **Generación rápida de perfiles de sitio web con VSPerfASPNETCmd**. **VSPerfASPNetCmd** es la herramienta de línea de comandos preferida cuando se utiliza el generador de perfiles independiente para generar perfiles de un sitio web de ASP.NET.  
  
## <a name="syntax"></a>Sintaxis  
 **vsperfaspnetcmd** [/*Opciones*] *Sitio web*  
  
## <a name="options"></a>Opciones  
  
|Opción|Descripción|  
|------------|-----------------|  
|**/Sample** o **/s**|Genera perfiles de sitios web utilizando el método de muestreo. **/Sample** es el método predeterminado. /Sample no se puede utilizar con **/Trace**.|  
|**/Trace** o **/t**|Genera perfiles de sitios web utilizando el método de instrumentación. /Trace no se puede utilizar con **/Sample**.|  
|**/Memory**[**:**`Type`]o **/m**[**:**{**a**&#124;**l**}]|Genera perfiles de asignación de memoria y opcionalmente de duraciones de objetos (recopilación de elementos no utilizados). **/Memory** se puede utilizar con el método de muestreo o de instrumentación.<br /><br /> El elemento *Type* puede ser uno de los siguientes:<br /><br /> -   **allocation** (o **a**) recopila únicamente datos de asignación de memoria.<br />-   **lifetime** (o **l**) recopila datos de asignación de memoria y de duración de objetos.<br /><br /> El valor predeterminado de `Type` es **allocation**.|  
|**/Tip** o **/i**|Agrega información detallada de solicitudes de ASP.NET y llamadas de ADO.NET a los datos de generación de perfiles. **/Tip** se puede utilizar con el método de muestreo o de instrumentación y con la opción **/Memory**.|  
|**/Output:** `File` o **/o:**`File`|Especifica la ruta de acceso y el nombre del archivo de datos de generación de perfiles (.vsp).|  
|**/NoWait** o  **/n**|Devuelve el símbolo del sistema inmediatamente para que los comandos adicionales se puedan utilizar en la ventana de símbolo del sistema. Para desactivar la generación de perfiles, debe escribir **VSPerfASPNETCmd /Shutdown** en una línea de comandos independiente.|  
|**/PackSymbols**[:{**on**&#124;**off**}or   **/p**[:{**on**&#124;**off**}|Inserta símbolos (nombres de función y parámetro, etc.) en el archivo de datos de generación de perfiles (.vsp).|  
|**/Shutdown:** `Website`o   **/d:**`Website`|Desactiva la generación de perfiles. Se utiliza como única opción en una línea de comandos después de utilizar la opción **/NoWait** para empezar a generar perfiles o si el generador de perfiles finaliza inesperadamente. Especifique la misma dirección URL que utilizó en el comando **VSPerfASPNETCmd** original.|  
|`Website`|La dirección URL del sitio web cuyo perfil se va a generar.|  
  
## <a name="see-also"></a>Vea también  
 [Generación rápida de perfiles de sitio web con VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)   
 [Generar perfiles para aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)

