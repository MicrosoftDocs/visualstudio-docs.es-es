---
title: "SCRIPTSTATE (enumeración) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: SCRIPTSTATE
apilocation: scrobj.dll
helpviewer_keywords: SCRIPTSTATE enum
ms.assetid: 5f5deb05-c4bb-4964-8077-e624c6b2a14e
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35e062a9c2f3076144063ffb77895c8a03ecc4ac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="scriptstate-enumeration"></a>SCRIPTSTATE (Enumeración)
Especifica el estado de un motor de scripting. Esta enumeración se usa en la [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) , [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) , y [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) métodos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
|SCRIPTSTATE_UNINITIALIZED|Secuencia de comandos se ha creado recientemente, pero aún no se ha inicializado con un `IPersist*` interfaz y [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) .|  
|SCRIPTSTATE_INITIALIZED|Secuencia de comandos se ha inicializado, pero no se ejecutan (conectarse a otros objetos o recibir eventos) o ejecutar cualquier código. Código que puede consultarse para la ejecución mediante una llamada a la [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md) método.|  
|SCRIPTSTATE_STARTED|Secuencia de comandos puede ejecutar código, pero no aún es recibir los eventos de los objetos agregados por el [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) método.|  
|SCRIPTSTATE_CONNECTED|Secuencia de comandos está cargado y conectado para recibir eventos.|  
|SCRIPTSTATE_DISCONNECTED|Secuencia de comandos se carga y tiene un estado de tiempo de ejecución, pero está desconectado temporalmente de recibir eventos.|  
|SCRIPTSTATE_CLOSED|Se ha cerrado la secuencia de comandos. El motor de scripting ya no funciona y devuelve errores con la mayoría de los métodos.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script (Constantes, Enumeraciones y Códigos de error)](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)