---
title: Constantes (Debug Interface Access SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- constants, DIA SDK
- DIA SDK, constants
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b10ab87f056bc153ec41c125b0e01ddefa139b80
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745398"
---
# <a name="constants-debug-interface-access-sdk"></a>Constantes (Debug Interface Access SDK)
Estas constantes de cadena se pueden usar para identificar varias secciones de un archivo de la base de datos de depuración del programa (PDB) a través del SDK de DIA.

## <a name="constants"></a>Constantes
Los siguientes elementos se declaranC++ como C/macros.

|Macro|Valor|
|-----------|-----------|
|`DiaTable_Symbols`|L "símbolos"|
|`DiaTable_Sections`|L "secciones"|
|`DiaTable_SrcFiles`|L "SourceFiles"|
|`DiaTable_LineNums`|L"LineNumbers"|
|`DiaTable_SegMap`|L "SegmentMap"|
|`DiaTable_Dbg`|L "dbg"|
|`DiaTable_InjSrc`|L "InjectedSource"|
|`DiaTable_FrameData`|L "FrameData"|

## <a name="example"></a>Ejemplo
Este es un ejemplo de uso de uno de estos símbolos:

```C++
HRESULT GetSymbolTable(IDiaEnumTables *pEnumTables, IDiaTable **pTable)
{
    HRESULT hr;
    VARIANT var;
    var.vt      = VT_BSTR;
    var.bstrVal = SysAllocString( DiaTable_Symbols );
    hr = pEnumTables->Item( var, pTable );
    return(hr);
}
```

## <a name="requirements"></a>Requisitos
Encabezado: Dia2. h

## <a name="see-also"></a>Vea también
- [Referencia](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)
- [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
