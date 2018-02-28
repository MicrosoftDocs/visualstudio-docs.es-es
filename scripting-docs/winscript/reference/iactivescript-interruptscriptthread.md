---
title: IActiveScript::InterruptScriptThread | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScript.InterruptScriptThread
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_InterruptScriptThread
ms.assetid: 2304d035-6d39-4811-acd3-8a9640fdbef6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad717ee950dda4f0f0d7a14292f0f5f150ab4973
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptinterruptscriptthread"></a>IActiveScript::InterruptScriptThread
Interrumpe la ejecución de un subproceso en ejecución de script (un receptor de eventos, una ejecución inmediata o una llamada de macro). Este método puede utilizarse para terminar una secuencia de comandos que se bloqueó (por ejemplo, en un bucle infinito). Se puede llamar desde subprocesos no sea de base sin que ello en una llamada no sea de base a los objetos de host o a la [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) método.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT InterruptScriptThread(  
    SCRIPTTHREADID   stidThread,  // identifier of thread  
    const EXCEPINFO *pexcepinfo,  // receives error information  
    DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `stidThread`  
 [in] Identificador del subproceso a interrupción, o a uno de los siguientes valores de identificador de subproceso especial:  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTTHREADID_ALL|Todos los subprocesos. La interrupción se aplica a todos los métodos de secuencia de comandos en curso. Tenga en cuenta que a menos que el llamador ha solicitado que van a desconectar la secuencia de comandos, el siguiente evento incluido en script hace que el código de script para volver a ejecutar mediante una llamada a la [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) método con el SCRIPTSTATE_DISCONNECTED o SCRIPTSTATE_INITIALIZED marca establecida.|  
|SCRIPTTHREADID_BASE|El subproceso base; es decir, se crea una instancia en el subproceso en el que el scripting del motor.|  
|SCRIPTTHREADID_CURRENT|El subproceso actualmente en ejecución.|  
  
 `pexcepinfo`  
 [in] Dirección de un `EXCEPINFO` estructura que contiene la información de error que se debería notificar a la secuencia de comandos anulada.  
  
 `dwFlags`  
 [in] Opción marcas asociadas a la interrupción. Puede ser uno de estos valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTINTERRUPT_DEBUG|Si se admite, escriba a depurador del motor de scripting en el momento de ejecución de script actual.|  
|SCRIPTINTERRUPT_RAISEEXCEPTION|Si se admite según el lenguaje del motor de scripting, dejar que el script controla la excepción. En caso contrario, se anulará el método de script y el código de error se devuelve al llamador; es decir, el evento origen o una macro invocador.|  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_POINTER`|Se especificó un puntero no válido.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting se aún no ha cargado o inicializar).|  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)