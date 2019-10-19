---
title: 'IActiveScript:: InterruptScriptThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.InterruptScriptThread
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_InterruptScriptThread
ms.assetid: 2304d035-6d39-4811-acd3-8a9640fdbef6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a436f973df05b945c0939f3a593640f567774277
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577263"
---
# <a name="iactivescriptinterruptscriptthread"></a>IActiveScript::InterruptScriptThread
Interrumpe la ejecución de un subproceso de script en ejecución (un receptor de eventos, una ejecución inmediata o una invocación de macro). Este método se puede usar para terminar un script que está atascado (por ejemplo, en un bucle infinito). Se puede llamar desde subprocesos no base sin tener como resultado una llamada no base a objetos host o al método [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT InterruptScriptThread(  
    SCRIPTTHREADID   stidThread,  // identifier of thread  
    const EXCEPINFO *pexcepinfo,  // receives error information  
    DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `stidThread`  
 de Identificador del subproceso que se va a interrumpir o uno de los siguientes valores de identificador de subproceso especial:  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTTHREADID_ALL|Todos los subprocesos. La interrupción se aplica a todos los métodos de script actualmente en curso. Tenga en cuenta que, a menos que el llamador haya solicitado que el script se desconecte, el siguiente evento con script hace que el código de script se ejecute de nuevo llamando al método [IActiveScript:: SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) con la marca SCRIPTSTATE_DISCONNECTED o SCRIPTSTATE_INITIALIZED conjunto.|  
|SCRIPTTHREADID_BASE|Subproceso base; es decir, el subproceso en el que se creó la instancia del motor de scripting.|  
|SCRIPTTHREADID_CURRENT|Subproceso que se está ejecutando actualmente.|  
  
 `pexcepinfo`  
 de Dirección de una estructura de `EXCEPINFO` que contiene la información de error que se debe informar al script anulado.  
  
 `dwFlags`  
 de Marcas de opciones asociadas a la interrupción. Puede ser uno de estos valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTINTERRUPT_DEBUG|Si se admite, especifique el depurador del motor de scripting en el punto de ejecución del script actual.|  
|SCRIPTINTERRUPT_RAISEEXCEPTION|Si el lenguaje del motor de scripting lo admite, deje que el script controle la excepción. De lo contrario, se anula el método de script y el código de error se devuelve al autor de la llamada. es decir, el origen de eventos o el invocador de macros.|  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los valores siguientes:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_POINTER`|Se ha especificado un puntero no válido.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting aún no se ha cargado o inicializado).|  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)