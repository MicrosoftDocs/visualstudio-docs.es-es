---
title: COMPUTER_INFO | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- COMPUTER_INFO structure
ms.assetid: 943085b2-f165-462d-9a4e-2086f0cdfff4
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1442e2762623731654acd287b95a68d05e40f517
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796368"
---
# <a name="computerinfo"></a>COMPUTER_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Se describe en el equipo donde se ejecuta el depurador.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
typedef struct tagCOMPUTER_INFO  
{  
    WORD wProcessorArchitecture;  
    WORD wSuiteMask;  
    DWORD dwOperatingSystemVersion;  
} COMPUTER_INFO;  
```  
  
```csharp  
public struct COMPUTER_INFO  
{  
    public ushort wProcessorArchitecture;  
    public ushort wSuiteMask;  
    public uint dwOperatingSystemVersion;  
}  
```  
  
## <a name="terms"></a>Términos  
 wProcessorArchitecture  
 Identifica la arquitectura del microprocesador.  
  
 wSuiteMask  
 Identifica la máscara del conjunto de aplicaciones.  
  
 dwOperatingSystemVersion  
 Número de versión del sistema operativo.  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura es devuelto por la [GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)

