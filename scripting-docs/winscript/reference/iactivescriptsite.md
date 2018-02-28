---
title: IActiveScriptSite | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSite interface
ms.assetid: 4d604a11-5365-46cf-ab71-39b3dbbe9f22
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c23dba403a7889fe46817a21ed8e4be65b1c05b4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsite"></a>IActiveScriptSite
Implementado por el host para crear un sitio para el motor de scripts de Windows. Normalmente, este sitio se asociará con el contenedor de todos los objetos que son visibles para la secuencia de comandos (por ejemplo, los controles de ActiveX). Normalmente, este contenedor se corresponderá con el documento o la página que se está visualizando. Por ejemplo, Microsoft Internet Explorer, crearía un contenedor de este tipo para cada página HTML que se va a mostrar. Cada ActiveX control (u otro objeto de automatización) en la página y el motor de scripting, sería enumerable dentro de este contenedor.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|||  
|-|-|  
|Método|Descripción|  
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|Recupera el identificador de configuración regional que usa el host para mostrar los elementos de la interfaz de usuario.|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|Obtiene información sobre un elemento que se ha agregado a un motor mediante una llamada a la [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) método.|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|Recupera una cadena definida por el host que identifica de forma única la versión actual del documento desde la perspectiva del host.|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|Se llama cuando la secuencia de comandos ha completado su ejecución.|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|Informa al host que el motor de scripting cambió los Estados.|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|Informa al host que se produjo un error de ejecución mientras el motor estaba ejecutando la secuencia de comandos.|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|Informa al host que el motor de scripting ha empezado a ejecutar el código de script.|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|Informa al host que ha devuelto el motor de scripting de ejecución de código de script.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script (Interfaces)](../../winscript/reference/active-script-interfaces.md)