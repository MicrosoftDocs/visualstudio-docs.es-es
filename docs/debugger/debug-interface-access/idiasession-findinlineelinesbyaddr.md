---
title: IDiaSession::findInlineeLinesByAddr | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: bb70e408-eed1-4c9c-b5b1-44323125f48b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 496f6b569b3ac02c625ddf18406b78fdb1687be2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742235"
---
# <a name="idiasessionfindinlineelinesbyaddr"></a>IDiaSession::findInlineeLinesByAddr
Recupera una enumeración que permite a un cliente recorrer en iteración la información del número de línea de todas las funciones insertadas, directa o indirectamente, por el símbolo primario especificado y que se encuentran dentro del intervalo de direcciones especificado.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT findInlineeLinesByAddr ( 
   IDiaSymbol*           parent,   DWORD                 isect,   DWORD                 offset,   DWORD                 length,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parámetros
 `parent`

de Objeto `IDiaSymbol` que representa el elemento primario.

 `isect`

de Especifica el componente de sección de la dirección.

 `offset`

de Especifica el componente de desplazamiento de la dirección.

 `length`

de Especifica el intervalo de direcciones, en número de bytes, que se va a cubrir con esta consulta.

 `ppResult`

enuncia Contiene un objeto `IDiaEnumLineNumbers` que contiene la lista de números de línea que se recuperan.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumeración SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)