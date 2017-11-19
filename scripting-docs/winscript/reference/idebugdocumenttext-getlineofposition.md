---
title: IDebugDocumentText::GetLineOfPosition | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentText.GetLineOfPosition
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentText::GetLineOfPosition
ms.assetid: fe8d4802-ea16-49ca-8973-89dcaf6c915b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2512fa3b56a19ed7396c7a351c8d8f8323fff6f5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttextgetlineofposition"></a>IDebugDocumentText::GetLineOfPosition
Devuelve el número de línea y, opcionalmente, el desplazamiento de caracteres dentro de la línea que corresponde a la posición de carácter especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetLineOfPosition(  
   ULONG   cCharacterPosition,  
   ULONG*  pcLineNumber,  
   ULONG*  pcCharacterOffsetInLine  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cCharacterPosition`  
 [in] Iniciar ubicación la posición del intervalo de caracteres.  
  
 `pcLineNumber`  
 [out] El número de línea del intervalo.  
  
 `pcCharacterOffsetInLine`  
 [entrada, salida] El desplazamiento de caracteres del intervalo en la línea `pcLineNumber`. Si este parámetro es `NULL`, el método no devuelve ningún valor.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve el número de línea y, opcionalmente, el desplazamiento de caracteres dentro de la línea que corresponde a la posición de carácter especificada.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentText (Interfaz)](../../winscript/reference/idebugdocumenttext-interface.md)