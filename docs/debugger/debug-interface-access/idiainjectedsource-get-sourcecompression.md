---
title: 'Idiainjectedsource:: Get_sourcecompression | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaInjectedSource::get_sourceCompression method
ms.assetid: 854b142f-23a9-466c-bf7f-98e581d5abcd
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cbf917a219443051da95634e8dc3263b3927c719
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idiainjectedsourcegetsourcecompression"></a>IDiaInjectedSource::get_sourceCompression
Recupera el indicador de la compresión de origen utilizado.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_sourceCompression (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve el indicador de la compresión de origen utilizado. Un valor de cero indica que se usa ninguna compresión de origen.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no se admite esta propiedad. De lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El valor devuelto por este método es específico del compilador que se utiliza. Por ejemplo, un compilador puede usar compresión de codificación de longitud de ejecución o estilo Huffman.  
  
## <a name="see-also"></a>Vea también  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)