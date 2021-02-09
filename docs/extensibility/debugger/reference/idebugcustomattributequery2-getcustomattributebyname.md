---
title: 'IDebugCustomAttributeQuery2:: Getcustomattributebyname (| Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8662e3c18f568e60ac98e5468acc3da28966505c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99842451"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Obtiene los atributos personalizados bytes dado el nombre del atributo personalizado.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetCustomAttributeByName( 
   LPCOLESTR pszCustomAttributeName,
   BYTE*     ppBlob,
   DWORD*    pdwLen
);
```

```csharp
int GetCustomAttributeByName(
   [In] string        pszCustomAttributeName,
   [In, Out] byte[]   ppBlob,
   [In, Out] ref uint pdwLen
);
```

## <a name="parameters"></a>Parámetros
`pszCustomAttributeName`\
de Cadena que contiene el nombre del atributo personalizado que se va a buscar.

`ppBlob`\
[in, out] Matriz que se rellena con los bytes de atributos personalizados.

`pdwLen`\
[in, out] Especifica el número máximo de bytes que se van a devolver en la `ppBlob` matriz y devuelve el número de bytes escritos realmente en la matriz.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, Devuelve S_OK o devuelve S_FALSE si el atributo personalizado no existe. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
 Establezca el `ppBlob` parámetro en un valor null para devolver el número de atributos bytes disponibles. A continuación, asigne una matriz y pase esa matriz en para el `ppBlob` parámetro.

 Los bytes de atributo representan los datos sin procesar del atributo personalizado.

 Si los `ppBlob` `pdwLen` parámetros y se establecen en un valor null, este método se puede utilizar para determinar si el atributo personalizado existe. Sin embargo, una alternativa más sencilla es llamar al método [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) .

## <a name="see-also"></a>Vea también
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
