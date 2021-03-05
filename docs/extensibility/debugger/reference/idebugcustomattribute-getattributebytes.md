---
description: Obtiene la información del atributo como un BLOB de bytes.
title: 'IDebugCustomAttribute:: GetAttributeBytes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d7cfc3ba650ff8277bb6cb85f5d1530d202bd426
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102163088"
---
# <a name="idebugcustomattributegetattributebytes"></a>IDebugCustomAttribute::GetAttributeBytes
Obtiene la información del atributo como un BLOB de bytes.

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
[in, out] Matriz que se rellena con los bytes de atributo.

`pdwLen`\
[in, out] Especifica el número máximo de bytes que se van a devolver en la `ppBlob` matriz y devuelve el número de bytes escritos realmente en la matriz.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Establezca el `ppBlob` parámetro en un valor null para devolver el número de atributos bytes disponibles. A continuación, asigne una matriz y pase esa matriz en para el `ppBlob` parámetro.

 Los bytes de atributo representan los datos sin procesar del atributo personalizado.

## <a name="see-also"></a>Consulte también
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
