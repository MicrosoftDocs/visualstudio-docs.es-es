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
ms.openlocfilehash: 88c9af8293dfc6a35e5f0e42d9596494d74b10aa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743682"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
Realiza el desenredo de la pila y devuelve los resultados en una interfaz de marco de recorrido de pila.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT execute ( 
   IDiaStackWalkFrame* frame
);
```

#### <a name="parameters"></a>Parámetros
 `frame`

de Un objeto [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) que contiene el estado de los registros de fotogramas.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. En la tabla siguiente se muestran los posibles valores devueltos para este método.

|Valor|Descripción|
|-----------|-----------------|
|E_DIA_INPROLOG|No se puede ejecutar un marco de pila en código de prólogo.|
|E_DIA_SYNTAX|Error de análisis detectado en el programa de marco.|
|E_DIA_FRAME_ACCESS|No se puede obtener acceso a los registros o a la memoria.|
|E_DIA_VALUE|Error en el cálculo de un valor (por ejemplo, división por cero).|

## <a name="remarks"></a>Comentarios
 Se llama a este método durante la depuración para desenredar la pila. El objeto [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) se implementa mediante la aplicación cliente para recibir actualizaciones de los registros y para proporcionar métodos utilizados por el método `execute`.

## <a name="see-also"></a>Vea también
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)