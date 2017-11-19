---
title: 'Idiasymbol:: Get_typeids | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ed742971a75d15eccfd6765dbaf242f0afc7890
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
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