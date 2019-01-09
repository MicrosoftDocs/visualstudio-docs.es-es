---
title: IDebugDocumentHelper::Detach | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.Detach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::Detach
ms.assetid: 820b9a8c-9a88-479a-b095-daea99394f9c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd86e1860cf4bd22a71b6f728ca36dbd3b7414a4
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089497"
---
# <a name="idebugdocumenthelperdetach"></a>IDebugDocumentHelper::Detach
Este documento se quita del árbol de documentos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Detach();  
```  
  
#### <a name="parameters"></a>Parámetros  
 Este método no toma ningún parámetro.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método quita este documento desde el árbol del documento.  
  
## <a name="see-also"></a>Vea también  
 [Idebugdocumenthelper](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [IDebugDocumentHelper (Interfaz)](../../winscript/reference/idebugdocumenthelper-interface.md)