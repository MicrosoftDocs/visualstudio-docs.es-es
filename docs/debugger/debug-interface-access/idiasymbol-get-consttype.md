---
title: 'Idiasymbol:: Get_consttype | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_constType method
ms.assetid: cb43605e-fa39-4f83-b047-f936a8019d03
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7ad00c80d3be6eab7bd69ec79d68aff47387aa6d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetconsttype"></a>IDiaSymbol::get_constType
Recupera una marca que especifica si el tipo de datos definido por el usuario es constante.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_constType (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve `TRUE` si el tipo de datos definido por el usuario es constante; en caso contrario, devuelve `FALSE`.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="requirements"></a>Requisitos  
  
|Requisito|Descripción|  
|-----------------|-----------------|  
|Encabezado:|dia2.h|  
|Versión:|SDK de DIA v7.0|  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)