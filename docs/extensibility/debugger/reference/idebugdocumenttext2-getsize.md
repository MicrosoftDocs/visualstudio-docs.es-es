---
title: IDebugDocumentText2::GetSize | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fe37c7157f96a905e52fb6656d5ebb8ff6f4971a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
Recupera el tamaño del texto en esta posición en el documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetSize(   
   ULONG* pcNumLines,  
   ULONG* pcNumChars  
);  
```  
  
```csharp  
int GetSize(   
   ref uint pcNumLines,  
   ref uint pcNumChars  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pcNumLines`  
 [out] Devuelve el número de líneas de texto.  
  
 `pcNumChars`  
 [out] Devuelve el número de caracteres de texto.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 [Solo en C++] Si no se desea un valor determinado, pase un valor NULL para el parámetro.  
  
 [Sólo en C#] Deben especificarse ambos parámetros.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)