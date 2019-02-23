---
title: IDebugDocumentText2::GetSize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3d5749a4bd738d6ec7edbf926542dbde0eb59db6
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685552"
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
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios

 [Solo en C++] Si no se desea un valor concreto, pase un valor NULL para el parámetro.


 [C# sólo] Se deben especificar ambos parámetros.

## <a name="see-also"></a>Vea también
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)