---
title: "IDiaSymbol::get_baseType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSymbol::get_baseType (método)"
ms.assetid: 5c69a241-a8d3-48ed-8b36-27463a196572
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IDiaSymbol::get_baseType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

recupera el tipo base para este símbolo*.*  
  
## Sintaxis  
  
```cpp#  
HRESULT get_baseType (   
   DWORD* pRetVal  
);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\]  Devuelve un valor de enumeración de [BasicType \(Enumeración\)](../../debugger/debug-interface-access/basictype.md) que especifica el tipo base de símbolos.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## Comentarios  
 El tipo básico para un token puede determinar primero obtiene el tipo de token y después interrogando a ese tipo devuelto para el tipo base.  Observe que algunos símbolos no puede tener una base \(por ejemplo, nombre de la estructura.  
  
## Ejemplo  
  
```cpp#  
IDiaSymbol* pType;  
CComPtr<IDiaSymbol> pBaseType;  
if (pType->get_type( &pBaseType ) == S_OK)  
{  
    BasicType btBaseType;  
    if (pBaseType->get_baseType((DWORD *)&btBaseType) == S_OK)  
    {  
        // Do something with basic type.  
    }  
}  
```  
  
## Requisitos  
  
|Requisito|Descripción|  
|---------------|-----------------|  
|encabezado:|dia2.h|  
|versión:|diámetro SDK v7.0|  
  
## Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [BasicType \(Enumeración\)](../../debugger/debug-interface-access/basictype.md)   
 [IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)