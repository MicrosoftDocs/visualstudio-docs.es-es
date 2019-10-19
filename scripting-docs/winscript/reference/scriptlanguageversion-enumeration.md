---
title: Enumeración SCRIPTLANGUAGEVERSION (| Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 58aa904a-e3ed-41c6-82d6-e91c8279a792
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 802a9f31cc7e3497c5e5fc54395d988552f75e84
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574360"
---
# <a name="scriptlanguageversion-enumeration"></a>SCRIPTLANGUAGEVERSION (Enumeración)
Especifica las versiones de scripting posibles.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION{    SCRIPTLANGUAGEVERSION_DEFAULT = 0,    SCRIPTLANGUAGEVERSION_5_7  = 1,    SCRIPTLANGUAGEVERSION_5_8  = 2,    SCRIPTLANGUAGEVERSION_MAX  = 255} SCRIPTLANGUAGEVERSION ;  
```  
  
## <a name="enumeration-values"></a>Valores de enumeración  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION_DEFAULT|La versión predeterminada. El valor entero es 0.|  
|SCRIPTLANGUAGEVERSION_5_7|Windows Scripting versión 5,7. El valor entero es 1.|  
|SCRIPTLANGUAGEVERSION_5_8|Windows Scripting versión 5,8. El valor entero es 2.|  
|SCRIPTLANGUAGEVERSION_MAX|Versión máxima. El valor entero es 255.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script (Constantes, Enumeraciones y Códigos de error)](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)