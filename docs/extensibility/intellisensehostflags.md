---
title: IntelliSenseHostFlags | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d8e00768e544dbd6bb37a4de70e0f730fe967a70
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
Especifica las marcas de host de IntelliSense.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum IntellisenseHostFlags  
{  
    IHF_READONLYCONTEXT      = 0x00000001  
    IHF_NOSEPARATESUBJECT    = 0x00000002  
    IHF_SINGLELINESUBJECT    = 0x00000004  
    IHF_FORCECOMMITTOCONTEXT = 0x00000008  
    IHF_OVERTYPE             = 0x00000010  
};  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Miembros|Descripción|  
|-------------|-----------------|  
|`IHF_READONLYCONTEXT`|Búfer de contexto es de solo lectura.|  
|`IHF_NOSEPARATESUBJECT`|Ningún texto de asunto. Búfer de contexto contiene IntelliSense y de destino (implica `!IHF_READONLYCONTEXT`).|  
|`IHF_SINGLELINESUBJECT`|Texto del asunto no es capaz varias líneas.|  
|`IHF_FORCECOMMITTOCONTEXT`|Igual a `CanCommitIntoReadOnlyBuffer`.|  
|`IHF_OVERTYPE`|Editar (en el asunto o el contexto) debe realizarse en el modo de sobrescribir.|  
  
## <a name="requirements"></a>Requisitos  
 SingleFileeditor.idl  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.TextManager.Interop>