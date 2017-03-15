---
title: "Restricciones en las longitudes de cadena | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "origen control complementos, restricciones en las longitudes de cadena"
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Restricciones en las longitudes de cadena
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La API de complementos de Control de código fuente limita las longitudes de cadenas usadas en distintas funciones.  
  
## Valores de longitud de cadena  
  
|Constante|Valor|  
|---------------|-----------|  
|`SCC_NAME_LEN`|31|  
|`SCC_AUXLABEL_LEN`|31|  
|`SCC_USER_LEN`|31|  
|`SCC_PRJPATH_LEN`|300|  
  
> [!NOTE]
>  La longitud no incluye el carácter final `null`. Otras constantes con un sufijo "\_SIZE" en lugar de "\_LEN" incluir espacio para la terminación `null`.  
  
|Constante|Valor|  
|---------------|-----------|  
|SCC\_NAME\_SIZE|32|  
|SCC\_AUXLABEL\_SIZE|32|  
|SCC\_USER\_SIZE|32|  
|SCC\_PRJPATH\_SIZE|301|  
  
## Vea también  
 [Complementos de Control de código fuente](../extensibility/source-control-plug-ins.md)