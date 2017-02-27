---
title: "IDiaEnumSegments | Microsoft Docs"
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
  - "IDiaEnumSegments (interfaz)"
ms.assetid: 0c9edd5e-b9ce-43e1-a791-cd4c5d16d923
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaEnumSegments
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Enumera los segmentos diferentes contenido en el origen de datos.  
  
## Sintaxis  
  
```  
IDiaEnumSegments : IUnknown  
```  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDiaEnumSegments`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDiaEnumSegments::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumsegments-get-newenum.md)|recupera la versión de [IEnumVARIANT Interface](http://msdn.microsoft.com/es-es/139e3c93-faef-4003-9079-e0e94494db3e) de este enumerador.|  
|[IDiaEnumSegments::get\_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md)|recupera el número de segmentos.|  
|[IDiaEnumSegments::Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)|recupera un segmento mediante un índice.|  
|[IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)|Recupera un número especificado de segmentos de la secuencia de la enumeración.|  
|[IDiaEnumSegments::Skip](../../debugger/debug-interface-access/idiaenumsegments-skip.md)|Omite un número especificado de segmentos en una secuencia de enumeración.|  
|[IDiaEnumSegments::Reset](../../debugger/debug-interface-access/idiaenumsegments-reset.md)|Restaura una secuencia de enumeración al principio.|  
|[IDiaEnumSegments::Clone](../../debugger/debug-interface-access/idiaenumsegments-clone.md)|Crea un enumerador que contiene al mismo estado de enumeración que el enumerador actual.|  
  
## Comentarios  
  
## Notas para los llamadores  
 Obtiene esta interfaz llamando al método de `QueryInterface` en un objeto de [IDiaTable](../../debugger/debug-interface-access/idiatable.md) .  Vea el ejemplo para obtener detalles.  
  
## Ejemplo  
 este ejemplo muestra cómo obtener la interfaz de `IDiaEnumSections` de una tabla.  Para obtener un ejemplo completo de segmentos mediante, vea la interfaz de [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) .  
  
```cpp#  
void ShowSegments(IDiaTable *pTable, IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSegments> pSegments;  
    if ( SUCCEEDED( pTable->QueryInterface(  
                                __uuidof( IDiaEnumSegments ),  
                                (void**)&pSegments )  
                  )  
       )  
    {  
        // Do something with this enumeration  
    }  
}  
```  
  
## Requisitos  
 encabezado: Dia2.h  
  
 biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Vea también  
 [Interfaces \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)