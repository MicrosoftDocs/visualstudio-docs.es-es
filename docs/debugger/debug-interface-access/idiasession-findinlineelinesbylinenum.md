---
title: IDiaSession::findInlineeLinesByLinenum | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cf32ae7c-a0c8-4800-bc8f-d64fdd15fb06
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 279ccc53176f0e1959ffb3ecd69fcbb39aa59dad
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942613"
---
# <a name="idiasessionfindinlineelinesbylinenum"></a>IDiaSession::findInlineeLinesByLinenum
Recupera una enumeración que permite que un cliente iterar por la información de número de línea de todas las funciones que están insertadas, directa o indirectamente, en el número de archivo y la línea de origen especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT findInlineeLinesByVA (   
   IDiaSymbol*           compiland,  
   IDiaSourceFile*       file,  
   DWORD                 linenum,  
   DWORD                 column,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `compiland`  
 [in] Un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto que representa la operación de compilación en el que se va a buscar los números de línea. Este parámetro no puede ser `NULL`.  
  
 `file`  
 [in] Un [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) objeto que representa el archivo de origen en el que se va a buscar. Este parámetro no puede ser `NULL`.  
  
 `linenum`  
 [in] Especifica un número de línea basado en uno.  
  
> [!NOTE]
>  No se puede usar cero para especificar todas las líneas (usar la [Findlines](../../debugger/debug-interface-access/idiasession-findlines.md) método para buscar todas las líneas).  
  
 `column`  
 [in] Especifica el número de columna. Usar cero para especificar todas las columnas. Una columna es un desplazamiento de bytes en una línea.  
  
 `ppResult`  
 [out] Devuelve un [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) objeto que contiene una lista de los números de línea que se han recuperado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum (enumeración)](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)