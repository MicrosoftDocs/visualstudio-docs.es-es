---
title: 'IDebugDocumentText2:: se obtiene | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: edc4a209537ca4bd54d3f6d9343d1496ab7c0e90
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731594"
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
Recupera el tamaño del texto en esta posición del documento.

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

## <a name="parameters"></a>Parámetros
`pcNumLines`\
enuncia Devuelve el número de líneas de texto.

`pcNumChars`\
enuncia Devuelve el número de caracteres de texto.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones

 [Solo C++] Si no se desea un valor determinado, pase un valor NULL para el parámetro.

 [Solo C#] Ambos parámetros deben especificarse.

## <a name="see-also"></a>Vea también
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
