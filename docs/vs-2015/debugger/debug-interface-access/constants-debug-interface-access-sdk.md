---
title: Constantes (Debug Interface Access SDK) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- constants, DIA SDK
- DIA SDK, constants
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dab1689d06332bd1c3ac93279289cfc002af0abc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777663"
---
# <a name="constants-debug-interface-access-sdk"></a>Constantes (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Estas constantes de cadena pueden utilizarse para identificar las distintas secciones de un archivo de base de datos (PDB) de depuración de programa a través del SDK de DIA.  
  
## <a name="constants"></a>Constantes  
 El siguiente se declara como macros de C o C++.  
  
|Macro|Valor|  
|-----------|-----------|  
|`DiaTable_Symbols`|L "Símbolos"|  
|`DiaTable_Sections`|L "Secciones"|  
|`DiaTable_SrcFiles`|L "SourceFiles"|  
|`DiaTable_LineNums`|L "LineNumbers"|  
|`DiaTable_SegMap`|L "SegmentMap"|  
|`DiaTable_Dbg`|L "Dbg"|  
|`DiaTable_InjSrc`|L "InjectedSource"|  
|`DiaTable_FrameData`|L "FrameData"|  
  
## <a name="example"></a>Ejemplo  
 Este es un ejemplo utilizando uno de estos símbolos:  
  
```cpp#  
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
 Encabezado: dia2.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)   
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)



