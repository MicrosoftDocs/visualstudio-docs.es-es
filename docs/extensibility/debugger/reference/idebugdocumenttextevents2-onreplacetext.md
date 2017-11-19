---
title: IDebugDocumentTextEvents2::onReplaceText | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocumentTextEvents2::OnReplaceText
helpviewer_keywords: IDebugDocumentTextEvents2::onReplaceText
ms.assetid: cb39f025-66d8-4dc0-bef6-1bdc8e07db92
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a278915878b032979e71e0463a38ea4f9ff1482c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdocumenttextevents2onreplacetext"></a>IDebugDocumentTextEvents2::onReplaceText
Notifica que el paquete de depuración que se ha reemplazado el texto en el documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT onReplaceText(   
   TEXT_POSITION pos,  
   DWORD         dwNumToReplace  
);  
```  
  
```csharp  
int onReplaceText(   
   enum_TEXT_POSITION pos,  
   uint               dwNumToReplace  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pos`  
 [in] A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) indica que se reemplazó el texto.  
  
 `dwNumToReplace`  
 [in] Especifica el número de caracteres de texto que se han reemplazado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)