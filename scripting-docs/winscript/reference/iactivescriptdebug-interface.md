---
title: IActiveScriptDebug (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 6341b5c3763d6e4c836b3bdc0539552fcbe7f980
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955034"
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