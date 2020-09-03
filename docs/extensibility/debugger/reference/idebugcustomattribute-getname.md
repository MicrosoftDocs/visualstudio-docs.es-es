---
title: 'IDebugCustomAttribute:: GetName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 15d435d043d0e3863358628fa12016431a417918
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732773"
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
enuncia Devuelve una cadena que contiene el nombre del atributo personalizado.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 El denominado devuelto por este método corresponde al nombre de la clase utilizada para declarar el atributo. Esto puede no corresponder exactamente al nombre de la propia clase de atributo personalizado como C# permite quitar el sufijo "Attribute" de un nombre de atributo personalizado cuando se usa en una declaración.

## <a name="see-also"></a>Vea también
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
