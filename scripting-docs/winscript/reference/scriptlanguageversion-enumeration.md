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
ms.openlocfilehash: e4cee2966b326ca7b4c258ffdb85b6fa71d90992
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734075"
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