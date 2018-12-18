---
title: IActiveScriptDebug (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptDebug interface
ms.assetid: e3e28cba-ee08-4a52-973a-b74be488c348
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0e21f4c99da886bc4907acf8b0934e1b46d57689
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942093"
---
# <a name="iactivescriptdebug-interface"></a>IActiveScriptDebug (Interfaz)
Implementado por los motores de scripts que admiten la depuración. Normalmente, un objeto que implementa el `IActiveScriptDebug` interfaz también implementa el `IActiveScript` interfaz. Si este es el caso, llame a la `IActiveScript::QueryInterface` método para obtener el `IActiveScriptDebug` interfaz.  
  
 El `IActiveScriptDebug` interfaz proporciona los medios para:  
  
- Hosts inteligentes para tomar el control de administración de documentos.  
  
- Administrador de depuración del proceso para sincronizar la depuración de varios motores de script.  
  
  Además de los métodos heredados de `IUnknown`, el `IActiveScriptDebug` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)|Devuelve los atributos de texto de un bloque de texto de la secuencia de comandos arbitrario.|  
|[IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)|Devuelve los atributos de texto para un scriptlet arbitrario.|  
|[IActiveScriptDebug::EnumCodeContextsOfPosition](../../winscript/reference/iactivescriptdebug-enumcodecontextsofposition.md)|Delega en `IDebugDocumentContext::EnumCodeContexts`.|