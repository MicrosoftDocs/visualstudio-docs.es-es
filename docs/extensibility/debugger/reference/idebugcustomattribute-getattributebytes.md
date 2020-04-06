---
title: IDebugCustomAttribute::GetAttributeBytes ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 621ebf3949a273e06053ced67209aa052c25bce0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732802"
---
# <a name="idebugcustomattributegetattributebytes"></a>IDebugCustomAttribute::GetAttributeBytes
Obtiene la información de atributo como un blob de bytes.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetAttributeBytes( 
   BYTE*  ppBlob,
   DWORD* pdwLen
);
```

```csharp
int GetAttributeBytes(
   ref byte[] ppBlob,
   ref uint   pdwLen
);
```

## <a name="parameters"></a>Parámetros
`ppBlob`\
[adentro, fuera] Matriz que se rellena con los bytes de atributo.

`pdwLen`\
[adentro, fuera] Especifica el número máximo de bytes `ppBlob` que se devolverán en la matriz y devuelve el número de bytes realmente escritos en la matriz.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Establezca `ppBlob` el parámetro en un valor nulo para devolver el número de bytes de atributos disponibles. A continuación, asigne una matriz `ppBlob` y pase esa matriz para el parámetro.

 Los bytes de atributo representan los datos sin procesar del atributo personalizado.

## <a name="see-also"></a>Vea también
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
