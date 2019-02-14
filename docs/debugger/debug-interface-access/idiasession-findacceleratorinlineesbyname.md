---
title: IDiaSession::findAcceleratorInlineesByName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c7814043b28e80e7c87543b94ef95e958434ddf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031258"
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
Devuelve una enumeración de los símbolos para los marcos en línea que corresponde al nombre de función en línea especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT findAcceleratorInlineeLinesByName (   
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `name`  
 [in] El nombre de función inlinee se va a buscar.  
  
 `option`  
 [in] Las opciones de búsqueda de nombre que se utilizará al buscar en línea los marcos que corresponden a `name`. Para obtener más información, consulte [NameSearchOptions (enumeración)](../../debugger/debug-interface-access/namesearchoptions.md).  
  
 `ppResult`  
 [out] Un puntero a un `IDiaEnumSymbols` puntero de interfaz que se inicializa con el resultado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Esta función busca inlinees solo dentro de las funciones de código auxiliar del acelerador. Omite los registros de procedimiento de C++ nativos.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)