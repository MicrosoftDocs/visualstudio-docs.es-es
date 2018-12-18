---
title: Get_addresssection | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressSection method
ms.assetid: fe80d479-3bb5-4f55-9b62-1bd58d0a60ce
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e62f6738d07b2f0e4463cd685bf3111cd7011a10
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49820031"
---
# <a name="idiasymbolgetaddresssection"></a>IDiaSymbol::get_addressSection
Recupera la parte de la sección de una dirección de ubicación. Cuando utilice el [LocationType (enumeración)](../../debugger/debug-interface-access/locationtype.md) está establecido en `LocIsStatic`.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_addressSection (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve la parte de la sección de una dirección de ubicación.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="remarks"></a>Comentarios  
 Los miembros estáticos ubicados en un archivo DLL externo, la sección devuelta por este método puede ser 0 como este método se basa en obtener la dirección virtual del miembro. Las direcciones virtuales son válidas solo si el [Put_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) método en el [IDiaSession](../../debugger/debug-interface-access/idiasession.md) interfaz se ha llamado con un parámetro distinto de cero que especifica la dirección de carga del archivo DLL.  
  
 Para obtener la parte de una dirección de desplazamiento, llame a la [Get_addressoffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md) método.  
  
## <a name="requirements"></a>Requisitos  
  
|Requisito|Descripción|  
|-----------------|-----------------|  
|Encabezado:|Dia2.h|  
|Versión:|SDK de DIA v7.0|  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeración LocationType](../../debugger/debug-interface-access/locationtype.md)