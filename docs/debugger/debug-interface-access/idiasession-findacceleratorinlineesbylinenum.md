---
title: IDiaSession::findAcceleratorInlineesByLinenum | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 386c87aa-f7b2-4d38-9dd6-fffba9ff01f0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b90a253baefad62bba205ccbf0fb8b8fff81712d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917471"
---
# <a name="idiasessionfindacceleratorinlineesbylinenum"></a>IDiaSession::findAcceleratorInlineesByLinenum
Devuelve una enumeración de los símbolos para los marcos flotantes que corresponden a la ubicación de origen especificado.  
  
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
 [in] Un `IDiaSymbol` que corresponde a la función de código auxiliar del acelerador que debe buscar.  
  
 `file`  
 [in] El `IDiaSourceFile` de la ubicación de origen.  
  
 `linenum`  
 [in] El número de línea de la ubicación de origen.  
  
 `colnum`  
 [in] El número de columna de la ubicación de origen.  
  
 `ppResult`  
 [out] Un puntero a un `IDiaEnumLineNumbers` puntero de interfaz que se inicializa con el resultado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)