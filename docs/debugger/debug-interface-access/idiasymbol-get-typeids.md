---
title: 'Idiasymbol:: Get_typeids | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 21c0aad37f51ca388c73ada62512887ff67e3e9a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idiasymbolgettypeids"></a>IDiaSymbol::get_typeIds
Recupera una matriz de valores de identificador de tipo específico de compilador para este símbolo.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_typeIds (   
   DWORD  cTypeIds,  
   DWORD* pcTypeIds,  
   DWORD  typeIds[]  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cTypeIds`  
 [in] Tamaño del búfer para almacenar los datos.  
  
 `pcTypeIds`  
 [out] Devuelve el número de `typeIds` escrito, o bien, si `typeIds` es `NULL`, a continuación, el número total de identificadores de tipo disponibles.  
  
 `typeIds[]`  
 [out] Una matriz que se rellenará con los identificadores de tipo.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)