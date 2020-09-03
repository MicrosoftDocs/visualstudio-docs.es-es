---
title: IDiaEnumSourceFiles::Next | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Next method
ms.assetid: 83bf6317-ff39-4c5c-8987-cba34e7a6983
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fe965043ad854c31c933447452f1039ba40cd04a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189813"
---
# <a name="idiaenumsourcefilesnext"></a>IDiaEnumSourceFiles::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera un número especificado de archivos de código fuente en la secuencia de enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Next (   
   ULONG            celt,  
   IDiaSourceFile** rgelt,  
   ULONG*           pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 celt  
 de El número de archivos de código fuente en el enumerador que se va a recuperar.  
  
 rgelt  
 enuncia Matriz que se va a rellenar con los objetos [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) que representan los archivos de código fuente deseados.  
  
 pceltFetched  
 enuncia Devuelve el número de archivos de código fuente en el enumerador recuperado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no hay más archivos de código fuente. De lo contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Consulte también  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSession:: findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
