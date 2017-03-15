---
title: "IDiaSymbol::get_virtualBaseTableType | Microsoft Docs"
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
  - "IDiaSymbol::get_virtualBaseTableType (método)"
ms.assetid: e0581c4f-0343-49b5-9754-a48477460e9f
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaSymbol::get_virtualBaseTableType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

recupera el tipo de un puntero virtual de la tabla base.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_virtualBaseTableType(  
   IDiaSymbol *pRetVal  
};  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`pRetVal`|\[out\]  Devuelve un objeto de [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que especifica el tipo de tabla base.|  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## Comentarios  
 Un puntero virtual de la tabla base \(`vbtptr`\) es un puntero oculto en [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] vtable que controla la herencia de clases base virtuales.  `vbtptr` puede tener distintos tamaños dependiendo de las clases heredadas.  
  
 Este método devuelve un objeto de [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que se puede utilizar para determinar el tamaño de vbtptr.  
  
## Requisitos  
  
|Requisito|Descripción|  
|---------------|-----------------|  
|encabezado:|dia2.h|  
|versión:|diámetro SDK v8.0|  
  
## Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)