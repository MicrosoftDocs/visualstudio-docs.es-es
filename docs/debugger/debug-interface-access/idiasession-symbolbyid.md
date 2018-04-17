---
title: 'Idiasession:: Symbolbyid | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symbolById method
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b4cafc8bf83c9c5e3a61712b6a3791bc234102c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idiasessionsymbolbyid"></a>IDiaSession::symbolById
Recupera un símbolo de por su identificador único.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT symbolById (   
   DWORD        id,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `id`  
 [in] Identificador único.  
  
 `ppSymbol`  
 [out] Devuelve un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) recupera el objeto que representa el símbolo.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El identificador especificado es un valor único que se usa internamente el SDK de DIA para hacer que todos los símbolos sea única.  
  
 Este método puede utilizarse, por ejemplo, para recuperar el símbolo que representa el tipo de otro símbolo (vea el ejemplo).  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo recupera una [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa el tipo de otro símbolo. Este ejemplo muestra cómo utilizar el `symbolById` método en la sesión. Un enfoque más sencillo consiste en llamar a la [idiasymbol:: Get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) método para recuperar el símbolo de tipo directamente.  
  
```C++  
IDiaSymbol *GetSymbolType(IDiaSymbol *pSymbol, IDiaSession *pSession)  
{  
    IDiaSymbol *pTypeSymbol = NULL;  
    if (pSymbol != NULL && pSession != NULL)  
    {  
        DWORD symbolTypeId;  
        pSymbol->get_typeId(&symbolTypeId);  
        pSession->symbolById(symbolTypeId, &pTypeSymbol);  
    }  
    return(pTypeSymbol);  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)