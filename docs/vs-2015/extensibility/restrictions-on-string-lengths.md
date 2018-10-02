---
title: Restricciones en las longitudes de cadena | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: aa5517445930b5d543148af68df7eeeb29fa8a22
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581828"
---
# <a name="restrictions-on-string-lengths"></a>Restricciones en las longitudes de cadena
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [restricciones en las longitudes de cadena](https://docs.microsoft.com/visualstudio/extensibility/restrictions-on-string-lengths).  
  
La API de complemento de Control de origen limita las longitudes de cadenas usadas en distintas funciones.  
  
## <a name="string-length-values"></a>Valores de longitud de cadena  
  
|Constante|Valor|  
|--------------|-----------|  
|`SCC_NAME_LEN`|31|  
|`SCC_AUXLABEL_LEN`|31|  
|`SCC_USER_LEN`|31|  
|`SCC_PRJPATH_LEN`|300|  
  
> [!NOTE]
>  La longitud no incluye el carácter final `null`. Otras constantes con un sufijo "_Tamaño" en lugar de "_LEN" incluir espacio para la terminación `null`.  
  
|Constante|Valor|  
|--------------|-----------|  
|SCC_NAME_SIZE|32|  
|SCC_AUXLABEL_SIZE|32|  
|SCC_USER_SIZE|32|  
|SCC_PRJPATH_SIZE|301|  
  
## <a name="see-also"></a>Vea también  
 [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)

