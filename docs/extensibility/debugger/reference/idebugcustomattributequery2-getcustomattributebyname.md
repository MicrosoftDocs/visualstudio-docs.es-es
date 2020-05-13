---
title: IDebugCustomAttributeQuery2::GetCustomAttributeByName ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 47471f2743e705b06fb9a1bda6752b24a7836d1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732567"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Obtiene los bytes de atributos personalizados dado el nombre del atributo personalizado.

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
[en] Cadena que contiene el nombre del atributo personalizado que se va a buscar.

`ppBlob`\
[adentro, fuera] Matriz que se rellena con los bytes de atributo personalizados.

`pdwLen`\
[adentro, fuera] Especifica el número máximo de bytes `ppBlob` que se devolverán en la matriz y devuelve el número de bytes realmente escritos en la matriz.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK o devuelve S_FALSE si el atributo personalizado no existe. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Establezca `ppBlob` el parámetro en un valor nulo para devolver el número de bytes de atributos disponibles. A continuación, asigne una matriz `ppBlob` y pase esa matriz para el parámetro.

 Los bytes de atributo representan los datos sin procesar del atributo personalizado.

 Si `ppBlob` los `pdwLen` parámetros y se establecen en un valor nulo, este método se puede utilizar para determinar si el atributo personalizado simplemente existe. Una alternativa más fácil, sin embargo, es llamar a la [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) método.

## <a name="see-also"></a>Vea también
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
