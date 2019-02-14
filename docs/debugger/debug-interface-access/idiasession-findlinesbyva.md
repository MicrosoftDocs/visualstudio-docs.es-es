---
title: IDiaSession::findLinesByVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByVA method
ms.assetid: f647eee9-a73c-483b-9fe9-21f42e560a7b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 063403df90ff222d13384ef61d865ba2c5187c9f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55000437"
---
# <a name="idiasessionfindlinesbyva"></a>IDiaSession::findLinesByVA
Recupera la información de número de línea para las líneas contenidas en un intervalo de direcciones virtual especificado (VA).  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT findLinesByVA (   
   ULONGLONG             va,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `va`  
 [in] Especifica la dirección como un jefe  
  
 `length`  
 [in] Especifica el número de bytes del intervalo de direcciones para cubrir con esta consulta.  
  
 `ppResult`  
 [out] Devuelve un [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) objeto que contiene una lista de la línea de todos los números que regulan el intervalo de direcciones especificado.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se muestra una función que obtiene todos los números de línea incluidos en una función mediante la dirección virtual de la función y la longitud.  
  
```C++  
IDiaEnumLineNumbers *GetLineNumbersByVA(IDiaSymbol *pFunc, IDiaSession *pSession)  
{  
    IDiaEnumLineNumbers* pEnum = NULL;  
    ULONGLONG            va;  
    ULONGLONG            length;  
  
    if (pFunc->get_virtualAddress ( &va ) == S_OK)  
    {  
        pFunc->get_length( &length );  
        pSession->findLinesByVA( va, static_cast<DWORD>( length ), &pEnum );  
    }  
    return(pEnum);  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)