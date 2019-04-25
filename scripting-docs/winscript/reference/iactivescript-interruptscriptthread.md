---
title: IActiveScript::InterruptScriptThread | Microsoft Docs
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
ms.openlocfilehash: aa46bc95087b3defaf739cc3473c58e29a93071c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155935"
---
# <a name="iactivescriptinterruptscriptthread"></a>IActiveScript::InterruptScriptThread
Interrumpe la ejecución de un subproceso en ejecución de script (un receptor de eventos, una ejecución inmediata o una llamada de macro). Este método puede usarse para terminar una secuencia de comandos que está bloqueada (por ejemplo, en un bucle infinito). Se puede llamar desde subprocesos no son de base sin resultante en una llamada que no sea de base a los objetos de host o a la [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) método.  
  
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
 [in] Identificador del subproceso para la interrupción, o uno de los siguientes valores de identificador de subproceso especial:  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTTHREADID_ALL|Todos los subprocesos. La interrupción se aplica a todos los métodos de script actualmente en curso. Tenga en cuenta que, a menos que el llamador ha solicitado que se ha desconectado la secuencia de comandos, el siguiente evento generado por script hace que el código de script para volver a ejecutar mediante una llamada a la [IActiveScript:: Setscriptstate](../../winscript/reference/iactivescript-setscriptstate.md) método con el SCRIPTSTATE_DISCONNECTED o SCRIPTSTATE_INITIALIZED marca establecida.|  
|SCRIPTTHREADID_BASE|El subproceso base; es decir, se crea una instancia en el subproceso en el que el scripting del motor.|  
|SCRIPTTHREADID_CURRENT|El subproceso actualmente en ejecución.|  
  
 `pexcepinfo`  
 [in] Dirección de un `EXCEPINFO` estructura que contiene la información de error que se informa al script anulado.  
  
 `dwFlags`  
 [in] Opción marcas asociadas a la interrupción. Puede ser uno de estos valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTINTERRUPT_DEBUG|Si se admite, escriba el depurador del motor de scripting en el punto de ejecución de script actual.|  
|SCRIPTINTERRUPT_RAISEEXCEPTION|Si se admite el lenguaje de scripting del motor, dejar que el script controle la excepción. En caso contrario, se anulará el método de script y el código de error se devuelve al llamador; es decir, el evento origen o macro invocador.|  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_POINTER`|Se especificó un puntero no válido.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting no se ha cargado o inicializado).|  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)