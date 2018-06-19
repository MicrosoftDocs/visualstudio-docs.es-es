---
title: IDiaSession::findInlineeLines | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b6822d8b-70d5-470b-8278-3aec4680326c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0b4db2b47963f6fe44cb5b8f974beb104e5398dc
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31468780"
---
# <a name="idiasessionfindinlineelines"></a>IDiaSession::findInlineeLines
Recupera una enumeración que permite a un cliente recorrer en iteración la información del número de línea de todas las funciones que se alinean, directamente o indirectamente, mediante el símbolo de elemento primario especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT findInlineeLines (   
   IDiaSymbol*       parent,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `parent`  
 [in] Un `IDiaSymbol` objeto que representa el elemento primario.  
  
 `ppResult`  
 [out] Contiene un `IDiaEnumLineNumbers` objeto que contiene la lista de números de línea que se recuperan.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum (enumeración)](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)