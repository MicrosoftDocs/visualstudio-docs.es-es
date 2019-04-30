---
title: IDebugApplicationNode100::GetExcludedDocuments | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100::GetExcludedDocuments
ms.assetid: d44583a7-0b0b-4799-b075-837ad1da1946
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b8b1793fc1a3aacb27cc612bb5212dc33e7ab7dc
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436041"
---
# <a name="idebugapplicationnode100getexcludeddocuments"></a>IDebugApplicationNode100::GetExcludedDocuments
Obtiene los documentos de texto que están ocultos por el filtro especificado.  
  
> [!IMPORTANT]
> [IDebugApplicationNode100 (interfaz)](../../winscript/reference/idebugapplicationnode100-interface.md) es implementada por PDM v10.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetExcludedDocuments(        [in] APPLICATION_NODE_EVENT_FILTER filter,        [out] TEXT_DOCUMENT_ARRAY* pDocuments        );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `filter`  
 El filtro.  
  
 `pDocuments`  
 El conjunto de documentos.  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplicationNode100 (Interfaz)](../../winscript/reference/idebugapplicationnode100-interface.md)