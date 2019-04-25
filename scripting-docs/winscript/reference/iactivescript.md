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
ms.openlocfilehash: 5b7e3a0172a798eab9a743f446dff3d339a785b2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151004"
---
# <a name="iactivescript"></a>IActiveScript
Proporciona los métodos necesarios para inicializar el motor de scripting. Debe implementar el motor de scripting el `IActiveScript` interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|Notifica al motor de scripting de la [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) sitio proporcionado por el host.|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|Recupera el objeto de sitio asociado con el motor de scripts de Windows.|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|Coloca el motor de scripting en el estado especificado.|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|Recupera el estado actual del motor de scripting.|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|Hace que el motor de scripting abandonar cualquier script cargado actualmente, pierden su estado y liberar los punteros de interfaz que tiene a otros objetos, escribir, por tanto, un estado cerrado.|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|Agrega el nombre de un elemento de nivel de raíz al espacio de nombres del motor de scripting.|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|Agrega una biblioteca de tipos para el espacio de nombres para la secuencia de comandos.|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|Recupera el `IDispatch` interfaz para el script en ejecución.|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|Recupera un identificador de scripting motor-definidas para el subproceso actualmente en ejecución.|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|Recupera un identificador de scripting motor-definido por el subproceso asociado al subproceso de Win32 de Microsoft especificado.|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|Recupera el estado actual de un subproceso de script.|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|Interrumpe la ejecución de un subproceso en ejecución del script.|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|Clona el motor de scripting actual (menos cualquier estado de ejecución actual), devolviendo un motor de scripting cargado que no tenga ningún sitio en el subproceso actual.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de interfaces de Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)