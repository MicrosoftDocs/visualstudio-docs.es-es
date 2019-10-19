---
title: 'IDebugDocumentText:: GetPositionOfContext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetPositionOfContext
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetPositionOfContext
ms.assetid: 90fec730-c3fb-45fb-92ef-05ecc90dca38
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da759eb98a6cdd28066ddaa8aafe785ede337a6e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572136"
---
# <a name="idebugdocumenttextgetpositionofcontext"></a>IDebugDocumentText::GetPositionOfContext
Devuelve el intervalo de posición de caracteres correspondiente a un contexto de documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetPositionOfContext(  
   IDebugDocumentContext*  psc,  
   ULONG*                  pcCharacterPosition,  
   ULONG*                  cNumChars  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `psc`  
 de Objeto de contexto del documento.  
  
 `pcCharacterPosition`  
 enuncia Ubicación de inicio del intervalo de posición de caracteres.  
  
 `cNumChars`  
 enuncia Número de caracteres del intervalo.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 El contexto de documento proporcionado a este método debe estar asociado a este documento.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentText (Interfaz)](../../winscript/reference/idebugdocumenttext-interface.md)