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
ms.openlocfilehash: f2f363b4a96ded547e701aaa9486f42f994d7e38
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54987013"
---
# <a name="idiasessionfindinlineelinesbyaddr"></a>IDiaSession::findInlineeLinesByAddr
Recupera una enumeración que permite que un cliente iterar por la información de número de línea de todas las funciones que se alinean, directamente o indirectamente, mediante el símbolo de elemento primario especificado y está dentro del intervalo de direcciones especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT findInlineeLinesByAddr (   
   IDiaSymbol*           parent,   DWORD                 isect,   DWORD                 offset,   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `parent`  
 [in] Un `IDiaSymbol` objeto que representa el elemento primario.  
  
 `isect`  
 [in] Especifica el componente de la sección de la dirección.  
  
 `offset`  
 [in] Especifica el componente de la dirección de desplazamiento.  
  
 `length`  
 [in] Especifica el intervalo de direcciones, en el número de bytes, para cubrir con esta consulta.  
  
 `ppResult`  
 [out] Contiene un `IDiaEnumLineNumbers` objeto que contiene la lista de números de línea que se recuperan.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeración SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)