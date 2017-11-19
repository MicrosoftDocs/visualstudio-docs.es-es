---
title: Interfaz IActiveScriptSiteDebug32 | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03f42217-303d-46e7-9792-61a5ab95252c
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: a752851aa6afd903747dc58fed79d2bc5b27e3e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebug32-interface"></a>Interfaz IActiveScriptSiteDebug32
Hosts inteligentes implementan la `IActiveScriptSiteDebug32` interfaz para realizar la administración de documentos y para participar en la depuración. El `IActiveScriptSite` objeto normalmente proporciona una implementación de la `IActiveScriptSiteDebug32` interfaz. Si es así, llame a la `IActiveScriptSite::QueryInterface` método para obtener el `IActiveScriptSiteDebug32` interfaz.  
  
 Además de los métodos heredados de `IUnknown`, el `IActiveScriptSiteDebug32` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptSiteDebug32::GetApplication](../../winscript/reference/iactivescriptsitedebug32-getapplication.md)|Devuelve el objeto de aplicación de depuración asociado a este sitio de la secuencia de comandos.|  
|[IActiveScriptSiteDebug32::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug32-getdocumentcontextfromposition.md)|Utilizado por el motor de lenguaje para delegar `IDebugCodeContext::GetSourceContext`.|