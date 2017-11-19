---
title: 'Idialoadcallback2:: Restrictoriginalpathaccess | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaLoadCallback2::RestrictOriginalPathAccess method
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 826cebba9d4eaf8e2bcf6d055a2ce524e1cf17d0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
Determina si es correcto para que busque un archivo .pdb en el directorio debug original.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT RestrictOriginalPathAccess ();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Cualquier código de retorno distinto de `S_OK` evita que busca un archivo .pdb en el directorio debug original. El directorio de depuración original es la ruta de acceso para el archivo de símbolos que se compilan en el archivo ejecutable cuando se activa la depuración. Esta ruta de acceso no es necesariamente el mismo que la ruta de acceso donde existe el archivo ejecutable.  
  
## <a name="see-also"></a>Vea también  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)