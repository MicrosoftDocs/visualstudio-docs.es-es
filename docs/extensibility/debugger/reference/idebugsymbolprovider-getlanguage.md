---
title: IDebugSymbolProvider::GetLanguage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetLanguage
helpviewer_keywords:
- IDebugSymbolProvider::GetLanguage method
ms.assetid: e4142183-3d8b-418f-907f-4ee4c753d8ce
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b20222db9b007fbeee6daf0df1921e4c56744818
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56699631"
---
# <a name="idebugsymbolprovidergetlanguage"></a>IDebugSymbolProvider::GetLanguage
Este método obtiene el idioma que se usa para compilar el código en la dirección de depuración.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetLanguage( 
   IDebugAddress* pAddress,
   GUID*          pguidLanguage,
   GUID*          pguidLanguageVendor
);
```

```csharp
int GetLanguage(
   IDebugAddress pAddress,
   out Guid      pguidLanguage,
   out Guid      pguidLanguageVendor
);
```

#### <a name="parameters"></a>Parámetros
 `pAddress`

 [in] Un objeto de la dirección representada por un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaz.

 `pguidLanguage`

 [out] Devuelve un `GUID` que especifica el lenguaje.

 `pguidLanguageVendor`

 [out] Devuelve un `GUID` que especifica el proveedor de lenguaje.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 El motor de depuración llama a este método para obtener la información que necesita seleccionar el evaluador de expresiones correcto.

## <a name="see-also"></a>Vea también
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)