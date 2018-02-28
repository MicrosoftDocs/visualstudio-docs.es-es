---
title: IVariantChangeType::ChangeType | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IVariantChangeType.ChangeType
apilocation:
- scrobj.dll
helpviewer_keywords:
- IVariantChangeType::ChangeType
ms.assetid: 52374764-c42e-49af-a219-ee00c535a118
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d742d1bd57c85aa75c9ccd60479d08c1a559fb37
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="ivariantchangetypechangetype"></a>IVariantChangeType::ChangeType
Toma un valor de tipo variant y crea una nueva variante con un tipo especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT ChangeType(  
   VARIANT*  pvarDst,  
   VARIANT*  pvarSrc,  
   LCID  lcid,  
   VARTYPE  vtNew  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pvarDst`  
 [entrada, salida] Una variante que contiene el valor representado por `pvarSrc`, pero con el tipo especificado por `vtNew`.  
  
 `pvarSrc`  
 [in] Un valor de tipo variant para cambiar a un nuevo tipo.  
  
 `lcid`  
 [in] El contexto de configuración regional que se utilizará al convertir los argumentos a o desde cadenas.  
  
 `vtNew`  
 [in] Especifica el tipo de `pvarDst` se convierta en.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 El `pvarDst` y `pvarSrc` los argumentos pueden ser iguales, en cuyo caso el valor original se sobrescribe. Este método pasa `pvarDst` a la `VariantClear` función y, por consiguiente, `pvarDst` debe inicializarse en un valor válido.  
  
## <a name="see-also"></a>Vea también  
 [IVariantChangeType (Interfaz)](../../winscript/reference/ivariantchangetype-interface.md)