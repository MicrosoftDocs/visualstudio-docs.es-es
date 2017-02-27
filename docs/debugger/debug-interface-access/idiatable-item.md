---
title: "IDiaTable::Item | Microsoft Docs"
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
  - "IDiaTable::Item (método)"
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaTable::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

recupera una referencia a la entrada especificada en la tabla.  
  
## Sintaxis  
  
```cpp#  
HRESULT Item (   
   DWORD      index,  
   IUnknown** element  
);  
```  
  
#### Parámetros  
 `index`  
 \[in\]  El índice de la entrada de tabla en el intervalo de 0 a `count`\-1, donde `count` es devuelto por el método de [IDiaTable::get\_Count](../../debugger/debug-interface-access/idiatable-get-count.md).  
  
 `element`  
 \[out\]  Devuelve un objeto de `IUnknown` que representa la entrada de tabla especificada.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 una tabla representa una colección de objetos.  Dependiendo de los objetos, el parámetro de elemento se puede convertir a la interfaz adecuada.  Por ejemplo, si una tabla contiene objetos de [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) , el parámetro de elemento puede estar la conversión a la interfaz de `IDiaSegment` .  
  
 Es un enfoque más común para llamar al método de `QueryInterface` en la interfaz de [IDiaTable](../../debugger/debug-interface-access/idiatable.md) para la interfaz adecuada de enumerador y utilizar los métodos específicos de enumerador para tener acceso a las tablas de contenido.  Vea la interfaz de [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) para obtener un ejemplo.  
  
## Vea también  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaTable::get\_Count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)