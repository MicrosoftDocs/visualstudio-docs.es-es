---
title: IDebugDocumentText::GetLineOfPosition | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetLineOfPosition
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetLineOfPosition
ms.assetid: fe8d4802-ea16-49ca-8973-89dcaf6c915b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d5d33a68b4bc87307281e37ff96f84834257a22
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58156013"
---
# <a name="idebugdocumenttextgetlineofposition"></a>IDebugDocumentText::GetLineOfPosition
Devuelve el número de línea y, opcionalmente, el desplazamiento de caracteres dentro de la línea que corresponde a la posición de carácter especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetLineOfPosition(  
   ULONG   cCharacterPosition,  
   ULONG*  pcLineNumber,  
   ULONG*  pcCharacterOffsetInLine  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cCharacterPosition`  
 [in] Inicie la ubicación de la posición del intervalo de caracteres.  
  
 `pcLineNumber`  
 [out] El número de línea del intervalo.  
  
 `pcCharacterOffsetInLine`  
 [in, out] El desplazamiento de caracteres del intervalo en la línea `pcLineNumber`. Si este parámetro es `NULL`, el método no devuelve un valor.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve el número de línea y, opcionalmente, el desplazamiento de caracteres dentro de la línea que corresponde a la posición de carácter especificada.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentText (Interfaz)](../../winscript/reference/idebugdocumenttext-interface.md)