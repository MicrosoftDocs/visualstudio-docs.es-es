---
title: IDebugDocumentTextEvents2::onInsertText | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocumentTextEvents2::OnInsertText
helpviewer_keywords: IDebugDocumentTextEvents2::onInsertText
ms.assetid: 6040181f-7288-4a42-953c-d23f74200431
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 669b37a18b642337e37420f553d822c6598614a1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdocumenttextevents2oninserttext"></a>IDebugDocumentTextEvents2::onInsertText
Notifica que el paquete de depuración que se ha insertado el texto en el documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT onInsert(   
   TEXT_POSITION pos,  
   DWORD         dwNumToInsert  
);  
```  
  
```csharp  
int onInsert(   
   enum_TEXT_POSITION pos,  
   uint               dwNumToInsert  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pos`  
 [in] A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) estructura que indica donde se insertó el texto.  
  
 `dwNumToInsert`  
 [in] Especifica el número de caracteres de texto que se han insertado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)