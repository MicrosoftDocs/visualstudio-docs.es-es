---
title: IDiaEnumSectionContribs::Skip | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Skip method
ms.assetid: 7471a178-5134-41b2-80a6-51ff96abe916
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 55dd45244779ca341a4228adf3256d42616e66d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189939"
---
# <a name="idiaenumsectioncontribsskip"></a>IDiaEnumSectionContribs::Skip
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Omite un número especificado de contribuciones de la sección en una secuencia de enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Skip(   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `celt`  
 de Número de contribuciones de la sección en la secuencia de enumeración que se va a omitir.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve si no hay `S_FALSE` más contribuciones de sección para omitir.  
  
## <a name="see-also"></a>Consulte también  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)
