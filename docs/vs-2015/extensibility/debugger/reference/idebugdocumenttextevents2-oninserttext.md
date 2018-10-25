---
title: IDebugDocumentTextEvents2::onInsertText | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDocumentTextEvents2::OnInsertText
helpviewer_keywords:
- IDebugDocumentTextEvents2::onInsertText
ms.assetid: 6040181f-7288-4a42-953c-d23f74200431
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 582d010128bc384cecfc316871f53e95082337d1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49833439"
---
# <a name="idebugdocumenttextevents2oninserttext"></a>IDebugDocumentTextEvents2::onInsertText
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Notifica el paquete de depuración que se ha insertado el texto en el documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 [in] Un [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) estructura que indica donde se insertó el texto.  
  
 `dwNumToInsert`  
 [in] Especifica el número de caracteres de texto que se insertaron.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)

