---
title: SCRIPTTRACEINFO (enumeración) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: cb8a4767-8c8e-4fa0-a735-038767a8c500
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 866f507b4d107c8f395be6588a85f67ea6bb45c9
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086754"
---
# <a name="scripttraceinfo-enumeration"></a>SCRIPTTRACEINFO (Enumeración)
Representa el evento de secuencia de comandos que se realiza un seguimiento. Utilizado en el [Iactivescriptsitetraceinfo método](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
typedef enum tagSCRIPTTRACEINFO {      SCRIPTTRACEINFO_SCRIPTSTART = 0,      SCRIPTTRACEINFO_SCRIPTEND   = 1,      SCRIPTTRACEINFO_COMCALLSTART    = 2,      SCRIPTTRACEINFO_COMCALLEND  = 3,      SCRIPTTRACEINFO_CREATEOBJSTART  = 4,      SCRIPTTRACEINFO_CREATEOBJEND    = 5,      SCRIPTTRACEINFO_GETOBJSTART = 6,      SCRIPTTRACEINFO_GETOBJEND   = 7,  } SCRIPTTRACEINFO ;  
```  
  
## <a name="enumeration-values"></a>Valores de enumeración  
  
|||  
|-|-|  
|SCRIPTTRACEINFO_SCRIPTSTART|Inicio de una secuencia de comandos.|  
|SCRIPTTRACEINFO_SCRIPTEND|Final de la secuencia de comandos.|  
|SCRIPTTRACEINFO_COMCALLSTART|El inicio de una llamada COM.|  
|SCRIPTTRACEINFO_COMCALLEND|El extremo de una llamada COM.|  
|SCRIPTTRACEINFO_CREATEOBJSTART|Inicio de creación de objetos.|  
|SCRIPTTRACEINFO_CREATEOBJEND|El extremo de creación de objetos.|  
|SCRIPTTRACEINFO_GETOBJSTART|El inicio de una llamada a GetObject.|  
|SCRIPTTRACEINFO_GETOBJEND|El extremo de una llamada a GetObject.|