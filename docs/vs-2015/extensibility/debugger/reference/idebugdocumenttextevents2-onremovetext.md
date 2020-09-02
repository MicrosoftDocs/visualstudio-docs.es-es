---
title: 'IDebugDocumentTextEvents2:: onRemoveText | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2::OnRemoveText
helpviewer_keywords:
- IDebugDocumentTextEvents2::onRemoveText
ms.assetid: 1ebeabb2-52a1-4ccc-83cd-9ae7c3541783
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1ff2f3685250d9a4f6cbad9c1341a5e17b0641b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149339"
---
# <a name="idebugdocumenttextevents2onremovetext"></a>IDebugDocumentTextEvents2::onRemoveText
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Notifica al paquete de depuración que se ha quitado el texto del documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 de Estructura de [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) que indica dónde se ha quitado el texto.  
  
 `dwNumToRemove`  
 de Especifica el número de caracteres de texto que se han quitado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
