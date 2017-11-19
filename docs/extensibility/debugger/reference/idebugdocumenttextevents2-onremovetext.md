---
title: IDebugDocumentTextEvents2::onRemoveText | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocumentTextEvents2::OnRemoveText
helpviewer_keywords: IDebugDocumentTextEvents2::onRemoveText
ms.assetid: 1ebeabb2-52a1-4ccc-83cd-9ae7c3541783
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f58be325e0e91a3d5347bdab052f91825f54a60c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdocumenttextevents2onremovetext"></a>IDebugDocumentTextEvents2::onRemoveText
Notifica que el paquete de depuración que se ha quitado el texto del documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT onRemoveText(   
   TEXT_POSITION pos,  
   DWORD         dwNumToRemove  
);  
```  
  
```csharp  
int onRemoveText(   
   enum_TEXT_POSITION pos,  
   uint               dwNumToRemove  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pos`  
 [in] A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) estructura que indica que se quitó el texto.  
  
 `dwNumToRemove`  
 [in] Especifica el número de caracteres de texto que se quitaron.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)