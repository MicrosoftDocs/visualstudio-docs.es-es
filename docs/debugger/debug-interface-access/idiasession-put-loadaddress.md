---
title: 'Idiasession:: Put_loadaddress | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: f4721ee818c4dc75d883c7accd2faa162521de13
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idiasessionputloadaddress"></a>IDiaSession::put_loadAddress
Establece la dirección de carga del archivo ejecutable que corresponde a los símbolos en este almacén de símbolos.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT put_loadAddress (   
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `NewVal`  
 [in] Carga la dirección del archivo ejecutable.  
  
## <a name="remarks"></a>Comentarios  
 Propiedades de dirección virtual (VA) de símbolos se calculan utilizando el valor de este método. Direcciones virtuales no se calculan a menos que esta propiedad se establece en distinto de cero.  
  
> [!NOTE]
>  Debe llamar a este método cuando llegue el [IDiaSession](../../debugger/debug-interface-access/idiasession.md) objeto y antes de empezar a usar el objeto si necesita usar las propiedades virtuales en los símbolos.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)