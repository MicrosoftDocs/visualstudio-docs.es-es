---
title: Restricciones en las longitudes de cadena | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a7abc4290f784808f98b2c5833c896866ab51799
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58988263"
---
# <a name="restrictions-on-string-lengths"></a>Restricciones en las longitudes de cadena
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
