---
title: IDiaSession::findAcceleratorInlineesByName | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc2b6c7a221cf495ecbc9c981b1a62eef40d0a24
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
Devuelve una enumeración de símbolos para marcos flotantes correspondiente al nombre de función especificado en línea.  
  
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
 [in] El nombre de la función incluido en las que buscar.  
  
 `option`  
 [in] Las opciones de búsqueda de nombre que se usarán al buscar en línea los marcos que corresponden a `name`. Para obtener más información, consulte [NameSearchOptions (enumeración)](../../debugger/debug-interface-access/namesearchoptions.md).  
  
 `ppResult`  
 [out] Un puntero a un `IDiaEnumSymbols` puntero de interfaz que se inicializa con el resultado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Esta función busca inlinees solo dentro de las funciones de código auxiliar de acelerador. Omite los registros de procedimiento de C++ nativo.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)