---
title: IDebugDocumentHost (interfaz) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentHost interface
ms.assetid: 2fed4220-b6a2-47c6-bf28-daad7dd5c42d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: adaeb98f18a052106036a91885696dd4b4760dea
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthost-interface"></a>IDebugDocumentHost (Interfaz)
Expone la funcionalidad específica del host, como el color de sintaxis, al depurador. El `IDebugDocumentHelper::SetDebugDocumentHost` método toma esta interfaz como un argumento.  
  
 Además de los métodos heredados de `IUnknown`, el `IDebugDocumentHost` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugDocumentHost::GetDeferredText](../../winscript/reference/idebugdocumenthost-getdeferredtext.md)|Devuelve un intervalo de caracteres que se han agregado mediante `IDebugDocumentHelper::AddDeferredText`, en el documento de host original.|  
|[IDebugDocumentHost::GetScriptTextAttributes](../../winscript/reference/idebugdocumenthost-getscripttextattributes.md)|Devuelve los atributos de texto de un bloque de texto del documento.|  
|[IDebugDocumentHost::OnCreateDocumentContext](../../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md)|Notifica al host que se va a crear un nuevo contexto de documento y permite que el host también pueden devolver un objeto que controla el nuevo contexto.|  
|[IDebugDocumentHost::GetPathName](../../winscript/reference/idebugdocumenthost-getpathname.md)|Devuelve la ruta de acceso completa (incluido el nombre de archivo) del archivo de origen del documento.|  
|[IDebugDocumentHost::GetFileName](../../winscript/reference/idebugdocumenthost-getfilename.md)|Devuelve el nombre del documento, sin información de ruta de acceso.|  
|[IDebugDocumentHost::NotifyChanged](../../winscript/reference/idebugdocumenthost-notifychanged.md)|Notifica al host que se ha guardado el archivo de código fuente del documento y que se debe actualizar su contenido.|