---
title: IDiaSymbol::get_addressOffset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressOffset method
ms.assetid: c15639b0-7f37-46c7-891b-40273b7f6319
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8fc13197f668f7e046ec8ffc40da246c04449e94
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402507"
---
# <a name="idiasymbolgetaddressoffset"></a>IDiaSymbol::get_addressOffset
Recupera la parte del ajuste de una dirección de ubicación. Cuando utilice el [LocationType (enumeración)](../../debugger/debug-interface-access/locationtype.md) está establecido en `LocIsStatic`.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_addressOffset ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parámetros
 `pRetVal`

[out] Devuelve la parte del ajuste de una dirección de ubicación.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.

> [!NOTE]
> Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.

## <a name="remarks"></a>Comentarios
 Los miembros estáticos ubicados en un archivo DLL externo, el desplazamiento devuelto por este método puede ser 0 como este método se basa en obtener la dirección virtual del miembro. Las direcciones virtuales son válidas solo si el [Put_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) método en el [IDiaSession](../../debugger/debug-interface-access/idiasession.md) interfaz se ha llamado con un parámetro distinto de cero que especifica la dirección de carga del archivo DLL.

 Para obtener la parte de la sección de una dirección, llame a la [Get_addresssection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md) método.

## <a name="requirements"></a>Requisitos

|Requisito|Descripción|
|-----------------|-----------------|
|Encabezado:|dia2.h|
|Versión:|SDK de DIA v7.0|

## <a name="see-also"></a>Vea también
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumeración LocationType](../../debugger/debug-interface-access/locationtype.md)
- [IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)
- [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)