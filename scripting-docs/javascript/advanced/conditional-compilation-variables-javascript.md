---
title: Variables de compilación condicional (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- conditional compilation, variables
ms.assetid: d6f9827d-c558-412c-8e68-de04c19c3d9d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 900a44dab0ad418cd2899af6423f78016c90fe2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569125"
---
# <a name="conditional-compilation-variables-javascript"></a>Variables de compilación condicional (JavaScript)
Las siguientes variables predefinidas se pueden usar con la compilación condicional. Si una variable no es **true**, no está definida y se comporta como `NaN` cuando se tiene acceso a ella.  
  
> [!WARNING]
>  La compilación condicional se admite en todas las versiones de Internet Explorer anteriores a Internet Explorer 11. A partir del modo estándar de Internet Explorer 11, y en las aplicaciones de [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)], no se admite la compilación condicional.  
  
## <a name="variables"></a>Variables  
  
|Variable|Descripción|  
|--------------|-----------------|  
|@_win32|Es true si se ejecuta en un sistema Win32.|  
|@_win16|Es true si se ejecuta en un sistema Win16.|  
|@_mac|Es true si se ejecuta en un sistema Apple Macintosh.|  
|@_alpha|Es true si se ejecuta en un procesador DEC Alpha.|  
|@_x86|Es true si se ejecuta en un procesador Intel.|  
|@_mc680x0|Es true si se ejecuta en un procesador Motorola 680x0.|  
|@_PowerPC|Es true si se ejecuta en un procesador Motorola PowerPC.|  
|@_jscript|Siempre es true.|  
|@_jscript_build|Contiene el número de compilación del motor de scripting de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].|  
|@_jscript_version|Contiene el número de versión de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] con el formato principal.secundario.|