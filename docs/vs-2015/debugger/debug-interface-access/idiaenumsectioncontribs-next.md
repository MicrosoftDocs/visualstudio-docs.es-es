---
title: Idiaenumsectioncontribs | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Next method
ms.assetid: a6bb2adb-ee6d-4f3c-ab5b-e89361c8880e
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 01b09f132d7afadc5462602bde2eeb0a3da3bead
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47579146"
---
# <a name="idiaenumsectioncontribsnext"></a>IDiaEnumSectionContribs::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Idiaenumsectioncontribs](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaenumsectioncontribs-next).  
  
Recupera un número especificado de las contribuciones de la sección de la secuencia de enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Next(   
   ULONG                celt,   
   IDiaSectionContrib** rgelt,  
   ULONG*               pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 celt  
 [in] El número de las contribuciones de la sección del enumerador que se va a recuperar.  
  
 rgelt  
 [out] Una matriz que se va a rellenar con el [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) objetos que representan las contribuciones de la sección deseada.  
  
 pceltFetched  
 [out] Devuelve el número de las contribuciones de la sección del enumerador que se capturan.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`. Devuelve `S_FALSE` si no hay ningún más contribuciones de sección. De lo contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)



