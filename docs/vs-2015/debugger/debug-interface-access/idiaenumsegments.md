---
title: IDiaEnumSegments | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments interface
ms.assetid: 0c9edd5e-b9ce-43e1-a791-cd4c5d16d923
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bfd82fa284e76ecbbc7553f83d98303dd1ff78ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684421"
---
# <a name="idiaenumsegments"></a>IDiaEnumSegments
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Enumera los distintos segmentos incluidos en el origen de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDiaEnumSegments : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 En la tabla siguiente se muestran los métodos de `IDiaEnumSegments` .  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDiaEnumSegments::get__NewEnum](../../debugger/debug-interface-access/idiaenumsegments-get-newenum.md)|Recupera la versión de la [interfaz IEnumVARIANT](https://msdn.microsoft.com/139e3c93-faef-4003-9079-e0e94494db3e) de este enumerador.|  
|[IDiaEnumSegments::get_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md)|Recupera el número de segmentos.|  
|[IDiaEnumSegments::Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)|Recupera un segmento por medio de un índice.|  
|[IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)|Recupera un número especificado de segmentos en la secuencia de enumeración.|  
|[IDiaEnumSegments::Skip](../../debugger/debug-interface-access/idiaenumsegments-skip.md)|Omite un número especificado de segmentos en una secuencia de enumeración.|  
|[IDiaEnumSegments::Reset](../../debugger/debug-interface-access/idiaenumsegments-reset.md)|Restablece una secuencia de enumeración al principio.|  
|[IDiaEnumSegments::Clone](../../debugger/debug-interface-access/idiaenumsegments-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|  
  
## <a name="remarks"></a>Observaciones  
  
## <a name="notes-for-callers"></a>Notas para llamadores  
 Obtenga esta interfaz llamando al `QueryInterface` método en un objeto [IDiaTable](../../debugger/debug-interface-access/idiatable.md) . Consulte el ejemplo para más información.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se muestra cómo obtener la `IDiaEnumSections` interfaz de una tabla. Para obtener un ejemplo más completo del uso de segmentos, vea la interfaz [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) .  
  
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
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Dia2. h  
  
 Biblioteca: diaguids. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Consulte también  
 [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
