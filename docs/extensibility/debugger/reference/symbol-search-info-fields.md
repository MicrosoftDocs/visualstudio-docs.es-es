---
title: SYMBOL_SEARCH_INFO_FIELDS Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SYMBOL_SEARCH_INFO_FIELDS
helpviewer_keywords:
- SYMBOL_SEARCH_INFO_FIELDS enumeration
ms.assetid: bce35af0-722d-46d4-afa6-eaae598c51ff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bf8a1ad8a5dabc663ef29f5f2c36fdf0fbd8b786
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713479"
---
# <a name="symbol_search_info_fields"></a>SYMBOL_SEARCH_INFO_FIELDS
Especifica el tipo de información de símbolo que se va a recuperar.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_SYMBOL_SEARCH_INFO_FIELDS
{
   SSIF_NONE                = 0x00000000,
   SSIF_VERBOSE_SEARCH_INFO = 0x00000001
};
typedef DWORD SYMBOL_SEARCH_INFO_FIELDS;
```

```csharp
public enum enum_SYMBOL_SEARCH_INFO_FIELDS
{
   SSIF_NONE                = 0x00000000,
   SSIF_VERBOSE_SEARCH_INFO = 0x00000001
};

```

## <a name="fields"></a>Fields
 `SSIF_NONE`\
 Indica que no hay banderas

 `SSIF_VERBOSE_SEARCH_INFO`\
 Devuelve todas las rutas de búsqueda utilizadas para buscar símbolos

## <a name="remarks"></a>Observaciones
 Estos indicadores se pasan como un parámetro a la [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) método para determinar la cantidad de información devuelta.

> [!NOTE]
> Actualmente, `SSIF_VERBOSE_SEARCH_INFO` solo se admite y debe `dwFlags` especificarse `IDebugModule3::GetSymbolInfo`como parámetro para . Todos los demás valores devuelven un error.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
