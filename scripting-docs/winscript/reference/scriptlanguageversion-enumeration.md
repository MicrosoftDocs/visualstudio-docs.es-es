---
title: SCRIPTLANGUAGEVERSION (enumeración) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 58aa904a-e3ed-41c6-82d6-e91c8279a792
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 374025b7564c058ae89064b6a27384c9075a30f9
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54350107"
---
# <a name="scriptlanguageversion-enumeration"></a>SCRIPTLANGUAGEVERSION (Enumeración)
Especifica las posibles secuencias de comandos de versiones.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION{    SCRIPTLANGUAGEVERSION_DEFAULT = 0,    SCRIPTLANGUAGEVERSION_5_7  = 1,    SCRIPTLANGUAGEVERSION_5_8  = 2,    SCRIPTLANGUAGEVERSION_MAX  = 255} SCRIPTLANGUAGEVERSION ;  
```  
  
## <a name="enumeration-values"></a>Valores de enumeración  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION_DEFAULT|La versión predeterminada. El valor entero es 0.|  
|SCRIPTLANGUAGEVERSION_5_7|La versión 5.7 de secuencias de comandos de Windows. El valor entero es 1.|  
|SCRIPTLANGUAGEVERSION_5_8|Versión 5.8 de secuencias de comandos de Windows. El valor entero es 2.|  
|SCRIPTLANGUAGEVERSION_MAX|La versión máxima. El valor entero es 255.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script (Constantes, Enumeraciones y Códigos de error)](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)