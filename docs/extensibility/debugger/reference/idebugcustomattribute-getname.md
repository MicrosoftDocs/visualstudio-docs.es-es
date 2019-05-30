---
title: IDebugCustomAttribute::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3ed7abc9682d0a9f56c50fe7510ed3f276a6bf5a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315205"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
Obtiene el nombre del atributo personalizado.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetName( 
   BSTR* bstrName
);
```

```csharp
int GetName(
   out string bstrName
);
```

## <a name="parameters"></a>Parámetros
`bstrName`\
[out] Devuelve una cadena que contiene el nombre del atributo personalizado.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Con el nombre devuelto por este método se corresponde con el nombre de la clase que se utiliza para declarar el atributo. Esto es posible que no corresponden exactamente en el nombre de la propia clase de atributo personalizado como C# permite que el sufijo "Attribute" al que se van a quitar de un nombre de atributo personalizado cuando se utiliza en una declaración.

## <a name="see-also"></a>Vea también
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)