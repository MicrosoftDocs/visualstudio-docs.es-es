---
title: IActiveScriptSite | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSite interface
ms.assetid: 4d604a11-5365-46cf-ab71-39b3dbbe9f22
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67e16e2825f03c9ae452e639d6a086bee584ac95
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152647"
---
# <a name="iactivescriptsite"></a>IActiveScriptSite
Implementado por el host para crear un sitio para el motor de scripts de Windows. Normalmente, este sitio se asociará con el contenedor de todos los objetos que son visibles para la secuencia de comandos (por ejemplo, los controles ActiveX). Normalmente, este contenedor se corresponderá con el documento o la página que se está viendo. Por ejemplo, Microsoft Internet Explorer, crearía un contenedor de este tipo para cada página HTML que se muestran. Cada ActiveX control (u otro objeto de automatización) en la página y el motor de scripting, sería enumerable dentro de este contenedor.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|||  
|-|-|  
|Método|Descripción|  
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|Recupera el identificador de configuración regional que usa el host para mostrar los elementos de la interfaz de usuario.|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|Obtiene información sobre un elemento que se ha agregado a un motor mediante una llamada a la [IActiveScript:: Addnameditem](../../winscript/reference/iactivescript-addnameditem.md) método.|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|Recupera una cadena definida por el host que identifica la versión actual del documento desde la perspectiva del host.|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|Se llama cuando el script ha completado su ejecución.|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|Informa al host que el motor de scripting ha cambiado los Estados.|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|Informa al host que se ha producido un error de ejecución mientras el motor estaba ejecutando la secuencia de comandos.|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|Informa al host que el motor de scripting ha empezado a ejecutar el código de script.|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|Informa al host que ha devuelto el motor de scripting de ejecutar código de script.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script (Interfaces)](../../winscript/reference/active-script-interfaces.md)