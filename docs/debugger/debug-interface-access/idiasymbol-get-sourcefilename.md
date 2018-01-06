---
title: 'Idiasymbol:: Get_sourcefilename | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_sourceFileName method
ms.assetid: 0f5dce88-829e-4df3-8acd-8d71076ad167
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4cddf0be9982b8b8e2e6914c3c91230bfb315f14
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetsourcefilename"></a>IDiaSymbol::get_sourceFileName
Recupera el nombre de archivo del archivo de origen de operación de compilación.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_sourceFileName (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve el nombre de archivo del archivo de origen de operación de compilación.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)