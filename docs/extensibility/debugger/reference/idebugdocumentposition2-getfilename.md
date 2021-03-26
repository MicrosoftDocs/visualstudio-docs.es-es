---
description: Obtiene el nombre de archivo del archivo de código fuente que contiene la posición del documento.
title: 'IDebugDocumentPosition2:: GetFileName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetFileName
helpviewer_keywords:
- IDebugDocumentPosition2::GetFileName
ms.assetid: d713635e-088f-465b-b26d-00ac971c9e86
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 48c0500e47d938185595086ccf5fa5b22a14ab26
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066469"
---
# <a name="idebugdocumentposition2getfilename"></a>IDebugDocumentPosition2::GetFileName
Obtiene el nombre de archivo del archivo de código fuente que contiene la posición del documento.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetFileName( 
   BSTR* pbstrFileName
);
```

```csharp
int GetFileName( 
   out string pbstrFileName
);
```

## <a name="parameters"></a>Parámetros
`pbstrFileName`\
enuncia Devuelve el nombre de archivo del archivo de código fuente.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Es posible que un archivo de código fuente no tenga siempre un nombre de archivo (por ejemplo, es posible que el archivo de origen no exista en el disco).

## <a name="see-also"></a>Consulte también
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
