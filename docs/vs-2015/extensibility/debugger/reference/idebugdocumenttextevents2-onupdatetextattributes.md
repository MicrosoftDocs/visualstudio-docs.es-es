---
title: IDebugDocumentTextEvents2::onUpdateTextAttributes | Documentos de Microsoft
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
- IDebugDocumentTextEvents2::OnUpdateTextAttributes
helpviewer_keywords:
- IDebugDocumentTextEvents2::onUpdateTextAttributes
ms.assetid: eb68d69a-1ad9-4ce4-84e1-40979ef16634
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 172fe17d0ff3093ce8988c1de0ba991aba5bc9a7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49197228"
---
# <a name="idebugdocumenttextevents2onupdatetextattributes"></a>IDebugDocumentTextEvents2::onUpdateTextAttributes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Notifica el paquete de depuración que se han actualizado los atributos de texto en el documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT onUpdateTextAttributes(   
   TEXT_POSITION pos,  
   DWORD         dwNumToUpdate  
);  
```  
  
```csharp  
int onUpdateTextAttributes(   
   enum_TEXT_POSITION pos,  
   uint               dwNumToUpdate  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pos`  
 [in] Un [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) estructura que indica dónde se actualizaron los atributos de texto.  
  
 `dwNumToUpdate`  
 [in] Especifica el número de caracteres de texto que se actualizaron.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)

