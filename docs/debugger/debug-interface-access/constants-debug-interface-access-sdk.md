---
title: "Constantes (Debug Interface Access SDK) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "constantes, SDK de DIA"
  - "SDK de DIA, constantes"
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Constantes (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Estas constantes de cadena se pueden utilizar para identificar diferentes secciones de un archivo de base de datos de depuración de programa \(PDB\) a través del diámetro SDK.  
  
## Constantes  
 los siguientes se declaran como macros de C\/C\+\+.  
  
|Macro|Valor|  
|-----------|-----------|  
|`DiaTable_Symbols`|l " símbolos”|  
|`DiaTable_Sections`|l " secciones”|  
|`DiaTable_SrcFiles`|l " SourceFiles”|  
|`DiaTable_LineNums`|l " LineNumbers”|  
|`DiaTable_SegMap`|l " SegmentMap”|  
|`DiaTable_Dbg`|l " Dbg”|  
|`DiaTable_InjSrc`|l " InjectedSource”|  
|`DiaTable_FrameData`|l " FrameData”|  
  
## Ejemplo  
 A continuación se muestra un ejemplo utilizando uno de estos símbolos:  
  
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
  
## Requisitos  
 encabezado: dia2.h  
  
## Vea también  
 [Referencia](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)   
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Interfaces \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)