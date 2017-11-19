---
title: 'Idiaenumsegments:: Skip | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumSegments::Skip method
ms.assetid: ec67039f-da8c-4e70-8db7-957d7d5281e8
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 72f327dc469eef73e560df6da83ce65c038cff0c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumsegmentsskip"></a>IDiaEnumSegments::Skip
Omite un número especificado de segmentos en una secuencia de enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 celt  
 [in] El número de segmentos en la secuencia de enumeración que se va a omitir.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` si no hay ningún más segmentos que se omiten.  
  
## <a name="see-also"></a>Vea también  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)