---
title: IActiveScriptSiteDebug (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebug interface
ms.assetid: 2557ee09-688b-4c03-a821-180c24dfa0e6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 339325686d2a98e34c6e9f96056612769a9e110e
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348313"
---
# <a name="iactivescriptsitedebug-interface"></a>IActiveScriptSiteDebug (Interfaz)
Hosts inteligentes implementan la `IActiveScriptSiteDebug` interfaz para realizar la administración de documentos y participar en la depuración. El `IActiveScriptSite` objeto normalmente proporciona una implementación de la `IActiveScriptSiteDebug` interfaz. Si esto sucede, llame a la `IActiveScriptSite::QueryInterface` método para obtener el `IActiveScriptSiteDebug` interfaz.  
  
 Además de los métodos heredados de `IUnknown`, el `IActiveScriptSiteDebug` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptSiteDebug::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)|Usa el motor de lenguaje para delegar `IDebugCodeContext::GetSourceContext`.|  
|[IActiveScriptSiteDebug::GetApplication](../../winscript/reference/iactivescriptsitedebug-getapplication.md)|Devuelve el objeto de aplicación de depuración asociado a este sitio de la secuencia de comandos.|  
|[IActiveScriptSiteDebug::GetRootApplicationNode](../../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)|Obtiene el nodo de la aplicación en qué secuencia de comandos se deben agregar documentos.|  
|[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)|Permite a un host inteligente determinar cómo controlar los errores de tiempo de ejecución.|