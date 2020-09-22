---
title: IDiaSession::findInlineeLinesByLinenum | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: cf32ae7c-a0c8-4800-bc8f-d64fdd15fb06
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d16bc6f3e2e8f190e3a26023407237509984cece
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842731"
---
# <a name="idiasessionfindinlineelinesbylinenum"></a>IDiaSession::findInlineeLinesByLinenum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera una enumeración que permite a un cliente recorrer en iteración la información del número de línea de todas las funciones insertadas, directa o indirectamente, en el archivo de código fuente y el número de línea especificados.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 de Objeto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa la operación de compilación en la que se van a buscar los números de línea. Este parámetro no puede ser `NULL`.  
  
 `file`  
 de Objeto [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) que representa el archivo de código fuente en el que se va a buscar. Este parámetro no puede ser `NULL`.  
  
 `linenum`  
 de Especifica un número de línea basado en uno.  
  
> [!NOTE]
> No se puede usar cero para especificar todas las líneas (use el método [IDiaSession:: findLines](../../debugger/debug-interface-access/idiasession-findlines.md) para buscar todas las líneas).  
  
 `column`  
 de Especifica el número de columna. Use cero para especificar todas las columnas. Una columna es un desplazamiento de bytes en una línea.  
  
 `ppResult`  
 enuncia Devuelve un objeto [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) que contiene una lista de los números de línea recuperados.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Consulte también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeración Symtagenum (](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
