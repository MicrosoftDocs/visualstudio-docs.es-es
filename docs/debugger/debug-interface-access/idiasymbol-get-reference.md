---
title: 'Idiasymbol:: Get_reference | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_reference method
ms.assetid: 6a97cb74-6a14-41fd-8e24-2a42d7a1e529
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 466b7662812afb0a0a86130f414088fd731ea025
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetreference"></a>IDiaSymbol::get_reference
Recupera una marca que especifica si un tipo de puntero es una referencia.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_reference (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve `TRUE` si un tipo de puntero es una referencia; en caso contrario, devuelve `FALSE`.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)