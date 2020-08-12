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
ms.openlocfilehash: dcf95f74e05ebff6e1cc430c32b9fd7bdb3b005f
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144667"
---
# <a name="iactivescriptsite"></a>IActiveScriptSite
Implementado por el host para crear un sitio para el motor de Windows Script. Normalmente, este sitio se asociará con el contenedor de todos los objetos que son visibles para el script (por ejemplo, los controles ActiveX). Normalmente, este contenedor se corresponderá con el documento o la página que se está viendo. Por ejemplo, Microsoft Internet Explorer crearía este tipo de contenedor para cada página HTML mostrada. Cada control ActiveX (u otro objeto de automatización) de la página, y el propio motor de scripts, sería Enumerable dentro de este contenedor.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|
|-|-|
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|Recupera el identificador de configuración regional que usa el host para mostrar los elementos de la interfaz de usuario.|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|Obtiene información sobre un elemento que se agregó a un motor a través de una llamada al método [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|Recupera una cadena definida por el host que identifica de forma única la versión del documento actual desde el punto de vista del host.|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|Se llama cuando el script ha finalizado la ejecución.|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|Informa al host de que el motor de scripting ha cambiado de estado.|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|Informa al host de que se ha producido un error de ejecución mientras el motor estaba ejecutando el script.|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|Informa al host de que el motor de scripting ha empezado a ejecutar el código de script.|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|Informa al host de que el motor de scripting ha devuelto la ejecución de código de script.|  
  
## <a name="see-also"></a>Consulte también  
 [Active Script (Interfaces)](../../winscript/reference/active-script-interfaces.md)