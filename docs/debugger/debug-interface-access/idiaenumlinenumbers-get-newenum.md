---
title: 'Idiaenumlinenumbers:: Get__newenum | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumLineNumbers::get__NewEnum method
ms.assetid: 8b15f76b-a431-4f60-8bed-3206256b0d10
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb25e9e4cc9c86195895d281d459623dfcf72144
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumlinenumbersgetnewenum"></a>IDiaEnumLineNumbers::get__NewEnum
Recupera el <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> versión de este enumerador.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pRetVal  
 [out] Devuelve el `IUnknown` interfaz que representa la <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> versión de este enumerador.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)