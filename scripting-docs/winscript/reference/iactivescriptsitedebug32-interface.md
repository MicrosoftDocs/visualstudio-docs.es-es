---
title: Interfaz IActiveScriptSiteDebug32 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 03f42217-303d-46e7-9792-61a5ab95252c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 2a55161f76fcd98b52ddb769c640aca0e903239b
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835269"
---
# <a name="iactivescriptsitedebug32-interface"></a>IActiveScriptSiteDebug32 (Interfaz)
Los hosts inteligentes implementan la `IActiveScriptSiteDebug32` interfaz para realizar la administración de documentos y participar en la depuración. `IActiveScriptSite`Normalmente, el objeto proporciona una implementación de la `IActiveScriptSiteDebug32` interfaz. Si se hace esto, llame al `IActiveScriptSite::QueryInterface` método para obtener la `IActiveScriptSiteDebug32` interfaz.  
  
 Además de los métodos heredados de `IUnknown` , la `IActiveScriptSiteDebug32` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptSiteDebug32::GetApplication](../../winscript/reference/iactivescriptsitedebug32-getapplication.md)|Devuelve el objeto de la aplicación de depuración asociado a este sitio de script.|  
|[IActiveScriptSiteDebug32::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug32-getdocumentcontextfromposition.md)|Lo usa el motor de lenguaje para delegar `IDebugCodeContext::GetSourceContext` .|