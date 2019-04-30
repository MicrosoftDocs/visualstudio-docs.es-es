---
title: SCRIPTSTATE (enumeración) | Documentos de Microsoft
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
ms.openlocfilehash: fe6a05c5e73d26a8daa9e46c317422d85d1c40be
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840166"
---
# <a name="scriptstate-enumeration"></a>SCRIPTSTATE (Enumeración)
Especifica el estado de un motor de scripting. Esta enumeración se utiliza en el [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) , [IActiveScript:: Setscriptstate](../../winscript/reference/iactivescript-setscriptstate.md) , y [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) métodos.  
  
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
|SCRIPTSTATE_UNINITIALIZED|Acaba de crear secuencias de comandos, pero no se ha inicializado con un `IPersist*` interfaz y [IActiveScript:: Setscriptsite](../../winscript/reference/iactivescript-setscriptsite.md) .|  
|SCRIPTSTATE_INITIALIZED|Secuencia de comandos se ha inicializado, pero no se ejecutan (conectarse a otros objetos o eventos de recepción) o ejecutar cualquier código. Se puede consultar para la ejecución de código mediante una llamada a la [iactivescriptparse:: Parsescripttext](../../winscript/reference/iactivescriptparse-parsescripttext.md) método.|  
|SCRIPTSTATE_STARTED|Secuencia de comandos puede ejecutar código, pero no se desactivaba aún los eventos de los objetos agregados por el [IActiveScript:: Addnameditem](../../winscript/reference/iactivescript-addnameditem.md) método.|  
|SCRIPTSTATE_CONNECTED|Script está cargado y conectado para eventos de recepción.|  
|SCRIPTSTATE_DISCONNECTED|Script está cargado y tiene un estado de tiempo de ejecución, pero está temporalmente desconectado de eventos de recepción.|  
|SCRIPTSTATE_CLOSED|Se cerró la secuencia de comandos. El motor de scripting ya no funciona y devuelve errores con la mayoría de los métodos.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script (Constantes, Enumeraciones y Códigos de error)](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)