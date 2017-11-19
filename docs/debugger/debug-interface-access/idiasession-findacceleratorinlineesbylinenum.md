---
title: IDiaSession::findAcceleratorInlineesByLinenum | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 386c87aa-f7b2-4d38-9dd6-fffba9ff01f0
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f465a4089d2d0503c953c39e914d1d15ceff0e0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessionfindacceleratorinlineesbylinenum"></a>IDiaSession::findAcceleratorInlineesByLinenum
Devuelve una enumeración de símbolos para marcos flotantes que corresponden a la ubicación de origen especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT findAcceleratorInlineeLinesByName (   
   IDiaSymbol*           parent,  
   IDiaSourceFile*       file,  
   DWORD                 linenum,  
   DWORD                 colnum,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `parent`  
 [in] Un `IDiaSymbol` que corresponda a la función de código auxiliar de aceleración que necesita que se buscará.  
  
 `file`  
 [in] El `IDiaSourceFile` de la ubicación de origen.  
  
 `linenum`  
 [in] El número de línea de la ubicación de origen.  
  
 `colnum`  
 [in] El número de columna de la ubicación de origen.  
  
 `ppResult`  
 [out] Un puntero a un `IDiaEnumLineNumbers` puntero de interfaz que se inicializa con el resultado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)