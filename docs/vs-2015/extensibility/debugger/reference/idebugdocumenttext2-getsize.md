---
title: IDebugDocumentText2::GetSize | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1f6d438db999e2e0b2aa85c45c0b38333238755e
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "58999840"
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera el tamaño del texto en esta posición en el documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 [Solo en C++] Si no se desea un valor concreto, pase un valor NULL para el parámetro.  
  
 [C# sólo] Se deben especificar ambos parámetros.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
