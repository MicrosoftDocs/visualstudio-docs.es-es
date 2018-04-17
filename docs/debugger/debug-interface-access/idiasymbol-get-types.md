---
title: 'Idiasymbol:: Get_types | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_types method
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7340e7b0c3512c8a453dc9af8cc9915235a425be
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idiasymbolgettypes"></a>IDiaSymbol::get_types
Recupera una matriz de tipos específicos de compilador para este símbolo.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_types (   
   DWORD       cTypes,  
   DWORD*      pcTypes,  
   IDiaSymbol* types[]  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cTypes`  
 [in] Tamaño del búfer para almacenar los datos.  
  
 `pcTypes`  
 [out] Devuelve el número de tipos escritos, o bien, si la `types` parámetro es `NULL`, a continuación, el número total de tipos disponibles.  
  
 `types[]`  
 [out] Una matriz que se va a rellenar en con el [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objetos que representan todos los tipos de este símbolo.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)