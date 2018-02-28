---
title: IActiveScriptSiteDebug (interfaz) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebug interface
ms.assetid: 2557ee09-688b-4c03-a821-180c24dfa0e6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9b36054deeceb0528fb7ea399cc41d8edbbb47e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebug-interface"></a>IActiveScriptSiteDebug (Interfaz)
Hosts inteligentes implementan la `IActiveScriptSiteDebug` interfaz para realizar la administración de documentos y para participar en la depuración. El `IActiveScriptSite` objeto normalmente proporciona una implementación de la `IActiveScriptSiteDebug` interfaz. Si es así, llame a la `IActiveScriptSite::QueryInterface` método para obtener el `IActiveScriptSiteDebug` interfaz.  
  
 Además de los métodos heredados de `IUnknown`, el `IActiveScriptSiteDebug` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptSiteDebug::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)|Utilizado por el motor de lenguaje para delegar `IDebugCodeContext::GetSourceContext`.|  
|[IActiveScriptSiteDebug::GetApplication](../../winscript/reference/iactivescriptsitedebug-getapplication.md)|Devuelve el objeto de aplicación de depuración asociado a este sitio de la secuencia de comandos.|  
|[IActiveScriptSiteDebug::GetRootApplicationNode](../../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)|Obtiene el nodo de aplicación en las secuencias de comandos deben agregarse documentos.|  
|[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)|Permite a un host inteligente determinar cómo tratar los errores de tiempo de ejecución.|