---
title: IActiveScriptSiteDebug32 (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03f42217-303d-46e7-9792-61a5ab95252c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: e7937311e01274570e34bd639a0dc5f68206a3aa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992439"
---
# <a name="iactivescriptsitedebug32-interface"></a>IActiveScriptSiteDebug32 (interfaz)
Hosts inteligentes implementan la `IActiveScriptSiteDebug32` interfaz para realizar la administración de documentos y participar en la depuración. El `IActiveScriptSite` objeto normalmente proporciona una implementación de la `IActiveScriptSiteDebug32` interfaz. Si esto sucede, llame a la `IActiveScriptSite::QueryInterface` método para obtener el `IActiveScriptSiteDebug32` interfaz.  
  
 Además de los métodos heredados de `IUnknown`, el `IActiveScriptSiteDebug32` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptSiteDebug32::GetApplication](../../winscript/reference/iactivescriptsitedebug32-getapplication.md)|Devuelve el objeto de aplicación de depuración asociado a este sitio de la secuencia de comandos.|  
|[IActiveScriptSiteDebug32::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug32-getdocumentcontextfromposition.md)|Usa el motor de lenguaje para delegar `IDebugCodeContext::GetSourceContext`.|