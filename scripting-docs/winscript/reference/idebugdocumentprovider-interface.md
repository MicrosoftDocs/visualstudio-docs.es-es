---
title: IDebugDocumentProvider (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentProvider interface
ms.assetid: 36510acf-1ef9-479c-a430-d3f09502f82c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d775deb153205d0e9a452775272285c67e74a210
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949869"
---
# <a name="idebugdocumentprovider-interface"></a>IDebugDocumentProvider (Interfaz)
Proporciona los medios para crear instancias de un documento a petición.  
  
## <a name="remarks"></a>Comentarios  
 Esto significa indirecta para crear instancias de un documento:  
  
- Permite que el documento que se va a cargar cuando sea necesario.  
  
- Permite que el objeto de documento que se debe incluir en el IDE del depurador.  
  
- Permite varias formas de tener acceso al mismo objeto de documento.  
  
  Esto separa el documento de su proveedor de forma eficaz y permite al proveedor transportar la información de contexto de tiempo de ejecución adicionales.  
  
  Además de los métodos heredados de `IDebugDocumentInfo`, el `IDebugDocumentProvider` interfaz expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugDocumentProvider::GetDocument](../../winscript/reference/idebugdocumentprovider-getdocument.md)|Hace que el documento que se creará una instancia si aún no existe.|