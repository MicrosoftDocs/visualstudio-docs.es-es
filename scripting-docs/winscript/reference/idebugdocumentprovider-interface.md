---
title: IDebugDocumentProvider (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 5632134c86b5aa0e3cb769a68d2d4cfd944ff35c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63008682"
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