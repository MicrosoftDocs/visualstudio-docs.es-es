---
title: IntelliSenseHostFlags | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 582dc76bfd8b76ffa4d3664ab3e28f95fe2cef50
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500019"
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
  
### <a name="parameters"></a>Parámetros  
  
|Miembros|Descripción|  
|-------------|-----------------|  
|`IHF_READONLYCONTEXT`|Búfer de contexto es de solo lectura.|  
|`IHF_NOSEPARATESUBJECT`|No hay texto de asunto. Búfer de contexto contiene el destino de IntelliSense (implica `!IHF_READONLYCONTEXT`).|  
|`IHF_SINGLELINESUBJECT`|Texto del asunto no es capaz varias líneas.|  
|`IHF_FORCECOMMITTOCONTEXT`|Igual a `CanCommitIntoReadOnlyBuffer`.|  
|`IHF_OVERTYPE`|Edición (en el asunto o el contexto) debe realizarse en modo de reemplazo.|  
  
## <a name="requirements"></a>Requisitos  
 SingleFileeditor.idl  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.TextManager.Interop>