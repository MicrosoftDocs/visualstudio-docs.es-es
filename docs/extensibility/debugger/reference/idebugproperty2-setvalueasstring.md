---
title: IDebugProperty2::SetValueAsString | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 310d2e3cd8c7f1caea4e245c7c591cd402afdaf4
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/09/2019
ms.locfileid: "65458883"
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
Establece el valor de una propiedad de una cadena determinada.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT SetValueAsString ( 
   LPCOLESTR pszValue,
   UINT      nRadix,
   DWORD     dwTimeout
);
```

```csharp
int SetValueAsString ( 
   string pszValue,
   uint   nRadix,
   uint   dwTimeout
);
```

## <a name="parameters"></a>Parámetros
 `pszValue`\

 [in] Una cadena que contiene el valor debe establecerse.

 `nRadix`\

 [in] Una base de la que se usará en la interpretación de toda la información numérica. Esto puede ser 0 para intentar determinar automáticamente la base.

 `dwTimeout`\

 [in] Especifica el tiempo máximo, en milisegundos para esperar antes de volver de este método. Use `INFINITE` para esperar indefinidamente.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve el código de error. En la tabla siguiente se muestra otros posibles valores.

|Valor|Descripción|
|-----------|-----------------|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|No se pudo convertir la cadena en un valor de propiedad o no se puede establecer el valor de propiedad.|
|`E_SETVALUE_VALUE_IS_READONLY`|La propiedad es de solo lectura.|

## <a name="see-also"></a>Vea también
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)