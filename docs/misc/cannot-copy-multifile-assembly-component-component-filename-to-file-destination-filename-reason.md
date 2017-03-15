---
title: "No se puede copiar el componente de ensamblado de m&#250;ltiples archivos &quot;nombre de archivo del componente&quot; en el archivo &quot;nombre del archivo de destino&quot;. &lt;causa&gt;. | Microsoft Docs"
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
  - "vs.tasklisterror.cannotcopyscattercomponent"
ms.assetid: 22f851fc-431b-4cdf-9de1-3a29727fa1e6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# No se puede copiar el componente de ensamblado de m&#250;ltiples archivos &quot;nombre de archivo del componente&quot; en el archivo &quot;nombre del archivo de destino&quot;. &lt;causa&gt;.
El componente especificado no se ha copiado en el directorio bin.  
  
 Algunos ensamblados constan de varios archivos. Este diagnóstico aparece cuando no se puede copiar en el directorio de ejecución un archivo que forma parte de un ensamblado de múltiples archivos.  
  
 Podrían existir distintos motivos para el error. Por ejemplo, que no haya suficiente espacio en el disco o que se haya alcanzado el límite MAX\_PATH para las longitudes de rutas de acceso. Además, un proceso, quizás Visual Studio, puede contener el componente que no se puede copiar.  
  
 **Para corregir este error**  
  
-   Compruebe si hay suficiente espacio libre en disco.  
  
-   Intente mover el proyecto a una carpeta con una longitud de ruta de acceso que sea menor que la de la carpeta de proyecto actual.  
  
-   Cambie el directorio de resultados a una carpeta con una longitud de ruta de acceso absoluta menor. Esto solo se aplica a proyectos cliente \(que no son del tipo web\).  
  
-   Reinicie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Vea también  
 [Depurar las aplicaciones Web: errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)