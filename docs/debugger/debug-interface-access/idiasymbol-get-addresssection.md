---
title: IDiaSymbol::get_addressSection | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressSection method
ms.assetid: fe80d479-3bb5-4f55-9b62-1bd58d0a60ce
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5a468fe6ee8a8d7d00bb2e6c261d50919a1dd764
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741076"
---
# <a name="idiasymbolget_addresssection"></a>IDiaSymbol::get_addressSection
Recupera la parte de la sección de una ubicación de dirección. Se usa cuando la [enumeración LocationType (](../../debugger/debug-interface-access/locationtype.md) se establece en `LocIsStatic`.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_addressSection ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parámetros
 `pRetVal`

enuncia Devuelve la parte de la sección de una ubicación de dirección.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` o un código de error.

> [!NOTE]
> Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.

## <a name="remarks"></a>Comentarios
 En el caso de los miembros estáticos que se encuentran en un archivo DLL externo, la sección devuelta por este método puede ser 0, ya que este método se basa en obtener la dirección virtual del miembro. Las direcciones virtuales solo son válidas si se ha llamado al método [IDiaSession::P ut_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) de la interfaz [IDiaSession](../../debugger/debug-interface-access/idiasession.md) con un parámetro distinto de cero que especifica la dirección de carga del archivo dll.

 Para obtener la parte de desplazamiento de una dirección, llame al método [IDiaSymbol:: get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md) .

## <a name="requirements"></a>Requisitos

|Requisito|Descripción|
|-----------------|-----------------|
|Encabezado:|dia2.h|
|Versión:|SDK de DIA v 7.0|

## <a name="see-also"></a>Vea también
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumeración LocationType](../../debugger/debug-interface-access/locationtype.md)