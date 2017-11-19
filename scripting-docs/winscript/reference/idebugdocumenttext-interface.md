---
title: IDebugDocumentText (interfaz) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugDocumentText interface
ms.assetid: 242bad79-9c0a-4a30-879a-9f43db4e022b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9522d1075cd796fb69f6abbc42adc2706a817fed
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttext-interface"></a>IDebugDocumentText (Interfaz)
Proporciona acceso a una versión de solo texto del documento de depuración. Esta interfaz usa las siguientes convenciones:  
  
-   Posiciones de caracteres y números de línea están basadas en cero.  
  
-   Posiciones de caracteres representan desplazamientos de caracteres; no se representan bytes o desplazamientos de word. Para Win32, una posición de carácter es un desplazamiento de Unicode.  
  
 Además de los métodos heredados de `IDebugDocument`, el `IDebugDocumentText` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugDocumentText::GetDocumentAttributes](../../winscript/reference/idebugdocumenttext-getdocumentattributes.md)|Devuelve los atributos del documento.|  
|[IDebugDocumentText::GetSize](../../winscript/reference/idebugdocumenttext-getsize.md)|Devuelve el número de líneas y el número de caracteres en el documento.|  
|[IDebugDocumentText::GetPositionOfLine](../../winscript/reference/idebugdocumenttext-getpositionofline.md)|Devuelve la posición del carácter correspondiente al primer carácter de una línea.|  
|[IDebugDocumentText::GetLineOfPosition](../../winscript/reference/idebugdocumenttext-getlineofposition.md)|Devuelve el número de línea y, opcionalmente, el desplazamiento de caracteres dentro de la línea que corresponde a la posición de carácter especificada.|  
|[IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)|Recupera los caracteres o los atributos de carácter asociados a un intervalo de posición de carácter.|  
|[IDebugDocumentText::GetPositionOfContext](../../winscript/reference/idebugdocumenttext-getpositionofcontext.md)|Devuelve el intervalo de posición de carácter que corresponde a un contexto de documento.|  
|[IDebugDocumentText::GetContextOfPosition](../../winscript/reference/idebugdocumenttext-getcontextofposition.md)|Crea un objeto de contexto de documento correspondiente al intervalo de posición de carácter proporcionado.|