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
ms.openlocfilehash: 262794718e238068cfd9a8e3fae5161b9fe8cc54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726255"
---
# <a name="idebugdocumentprovider-interface"></a>IDebugDocumentProvider (Interfaz)
Proporciona los medios para crear instancias de un documento a petición.  
  
## <a name="remarks"></a>Comentarios  
 Esto significa indirecta para crear instancias de un documento:  
  
-   Permite que el documento que se va a cargar cuando sea necesario.  
  
-   Permite que el objeto de documento poder estar contenidos dentro del depurador de IDE.  
  
-   Permite varias formas de obtener acceso al mismo objeto de documento.  
  
 Esto eficazmente separa el documento de su proveedor y permite al proveedor transportar la información de contexto de tiempo de ejecución, adicionales.  
  
 Además de los métodos heredados de `IDebugDocumentInfo`, el `IDebugDocumentProvider` interfaz expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugDocumentProvider::GetDocument](../../winscript/reference/idebugdocumentprovider-getdocument.md)|Hace que el documento que se creará una instancia si aún no existe.|