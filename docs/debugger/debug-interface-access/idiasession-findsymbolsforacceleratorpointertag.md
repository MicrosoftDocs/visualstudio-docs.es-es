---
title: IDiaSession::findSymbolsForAcceleratorPointerTag | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 95fd5e7a-c637-437e-b369-c864eef733c2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 14a601143161ed17961ae5efd22cdc14c3fbb923
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54924394"
---
# <a name="idiasessionfindsymbolsforacceleratorpointertag"></a>IDiaSession::findSymbolsForAcceleratorPointerTag
Devuelve una enumeración de símbolos de la variable que el valor de etiqueta especificado corresponde de la principal función de código auxiliar del acelerador.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT findSymbolsForAcceleratorPointerTag (   
   IDiaSymbol*           parent,  
   DWORD                 tagValue,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `parent`  
 [in] Un IDiaSymbol que corresponde a la función de código auxiliar de acelerador se va a buscar.  
  
 `tagValue`  
 [in] El valor de etiqueta de puntero.  
  
 `ppResult`  
 [out] Un puntero a un `IDiaEnumSymbols` puntero de interfaz que se inicializa con el resultado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)