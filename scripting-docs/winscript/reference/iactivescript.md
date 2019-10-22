---
title: IActiveScript | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScript interface
ms.assetid: d8acee11-7f0d-4999-b97a-66774af16f71
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7a33db2bcbcb356a508fec2e6bc5449a899a1299
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577236"
---
# <a name="iactivescript"></a>IActiveScript
Proporciona los métodos necesarios para inicializar el motor de scripting. El motor de scripting debe implementar la interfaz `IActiveScript`.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|Informa al motor de scripting del sitio [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) proporcionado por el host.|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|Recupera el objeto de sitio asociado al motor de Windows Script.|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|Coloca el motor de scripting en el estado especificado.|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|Recupera el estado actual del motor de scripting.|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|Hace que el motor de scripting abandone cualquier script cargado actualmente, pierda su estado y libere los punteros de interfaz que tenga en otros objetos, con lo que se especifica un estado cerrado.|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|Agrega el nombre de un elemento de nivel de raíz al espacio de nombres del motor de scripting.|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|Agrega una biblioteca de tipos al espacio de nombres para el script.|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|Recupera la interfaz de `IDispatch` para el script en ejecución.|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|Recupera un identificador definido por el motor de scripting para el subproceso que se está ejecutando actualmente.|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|Recupera un identificador definido por el motor de scripting para el subproceso asociado al subproceso de Microsoft Win32 determinado.|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|Recupera el estado actual de un subproceso de script.|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|Interrumpe la ejecución de un subproceso de script en ejecución.|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|Clona el motor de scripting actual (menos cualquier estado de ejecución actual) y devuelve un motor de scripting cargado que no tiene ningún sitio en el subproceso actual.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de interfaces de Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)