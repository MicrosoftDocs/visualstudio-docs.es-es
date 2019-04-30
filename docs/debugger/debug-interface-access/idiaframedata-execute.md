---
title: IDiaFrameData::execute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78440c703ece2aa54e54594d57156dbb17848915
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62832676"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
Realiza el desenredo de pila y devuelve los resultados en una interfaz de marco de recorrido de pila.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT execute ( 
   IDiaStackWalkFrame* frame
);
```

#### <a name="parameters"></a>Parámetros
 `frame`

[in] Un [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) objeto que contiene el estado de los registros de marco.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. En la tabla siguiente se muestra los posibles valores devueltos para este método.

|Valor|Descripción|
|-----------|-----------------|
|E_DIA_INPROLOG|No se puede ejecutar un marco de pila en el código de prólogo.|
|E_DIA_SYNTAX|Analizar el error en el programa de marco.|
|E_DIA_FRAME_ACCESS|No se puede a los registros de acceso o la memoria.|
|E_DIA_VALUE|Error en el cálculo de un valor (por ejemplo, la división por cero).|

## <a name="remarks"></a>Comentarios
 Este método se llama durante la depuración para desenredar la pila. El [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) objeto es implementado por la aplicación de cliente para recibir actualizaciones de los registros y para proporcionar los métodos usados por la `execute` método.

## <a name="see-also"></a>Vea también
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)