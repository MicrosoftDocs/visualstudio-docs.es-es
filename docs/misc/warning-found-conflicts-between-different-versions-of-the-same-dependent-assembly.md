---
title: "Advertencia: Se encontraron conflictos entre diferentes versiones del mismo ensamblado dependiente | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ResolveAssemblyReference.SuggestedRedirects"
ms.assetid: fd14a789-bbdf-46c7-bcd3-9d3165adf96d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Advertencia: Se encontraron conflictos entre diferentes versiones del mismo ensamblado dependiente
Esta advertencia muestra si el gráfico de dependencias de su proyecto contiene referencias a versiones diferentes del mismo ensamblado.  
  
 Si tiene un archivo app.config, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permite agregar una redirección de enlace a él.  Una redirección de enlace obliga a todas las referencias del ensamblado a redirigirse a la versión más reciente del ensamblado. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] guarda la información de la redirección en app.config.  Si utiliza una redirección de enlace, esta advertencia no volverá a aparecer.  
  
 Si decide no agregar una redirección de enlace, su proyecto continuará haciendo referencia a la misma versión del ensamblado que antes.  Sin embargo, esta advertencia continuará apareciendo.  
  
### Para corregir este error  
  
-   Haga doble clic en la advertencia y, a continuación, seleccione "Sí" cuándo aparezca el mensaje "¿Desea resolver estos conflictos agregando registros de redireccionamiento de enlace al archivo app.config?"