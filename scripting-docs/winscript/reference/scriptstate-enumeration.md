---
title: Enumeración SCRIPTSTATE (| Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTSTATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTSTATE enum
ms.assetid: 5f5deb05-c4bb-4964-8077-e624c6b2a14e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10dd6366e2d0783ec2e9d6bdadc001e9f999901e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575678"
---
# <a name="scriptstate-enumeration"></a>SCRIPTSTATE (Enumeración)
Especifica el estado de un motor de scripting. Esta enumeración la usan los métodos [IActiveScript:: GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) , [IActiveScript:: SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) y [IActiveScriptSite:: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) .  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
typedef enum tagSCRIPTSTATE {  
    SCRIPTSTATE_UNINITIALIZED = 0,  
    SCRIPTSTATE_INITIALIZED   = 5,  
    SCRIPTSTATE_STARTED       = 1,  
    SCRIPTSTATE_CONNECTED     = 2,  
    SCRIPTSTATE_DISCONNECTED  = 3,  
    SCRIPTSTATE_CLOSED        = 4  
} SCRIPTSTATE;  
```  
  
## <a name="enumeration-values"></a>Valores de enumeración  
  
|||  
|-|-|  
|SCRIPTSTATE_UNINITIALIZED|El script se ha creado recientemente, pero aún no se ha inicializado con una interfaz `IPersist*` y [IActiveScript:: SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) .|  
|SCRIPTSTATE_INITIALIZED|El script se ha inicializado, pero no se está ejecutando (se está conectando a otros objetos o receptores de eventos) o ejecutando código. Se puede consultar el código para su ejecución mediante una llamada al método [IActiveScriptParse::P arsescripttext](../../winscript/reference/iactivescriptparse-parsescripttext.md) .|  
|SCRIPTSTATE_STARTED|El script puede ejecutar código, pero aún no está receptorando los eventos de objetos agregados por el método [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .|  
|SCRIPTSTATE_CONNECTED|El script se carga y se conecta para recibir eventos.|  
|SCRIPTSTATE_DISCONNECTED|El script está cargado y tiene un estado de ejecución en tiempo de ejecución, pero está desconectado temporalmente de los eventos de recepción.|  
|SCRIPTSTATE_CLOSED|El script se ha cerrado. El motor de scripting ya no funciona y devuelve errores con la mayoría de los métodos.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script (Constantes, Enumeraciones y Códigos de error)](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)