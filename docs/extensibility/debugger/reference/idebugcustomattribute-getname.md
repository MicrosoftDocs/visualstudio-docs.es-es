---
description: Obtiene el nombre del atributo personalizado.
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
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 313408639b0a93faef0c63c0add92dc1ca2e947b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102163062"
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

## <a name="see-also"></a>Consulte también
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
