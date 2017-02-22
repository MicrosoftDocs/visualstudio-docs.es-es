---
title: "Directiva de plantilla y la ventana Propiedades | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ventana de propiedades, directivas de plantilla"
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Directiva de plantilla y la ventana Propiedades
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cuando un proyecto se contiene dentro de un proyecto de plantilla de empresa, ese proyecto de plantilla de empresa puede aplicar la directiva.  La directiva de plantilla se convierte en un sistema que restringe que se puede utilizar para establecer los valores predeterminados de las propiedades, ocultar propiedades, agregue propiedades, etc.  
  
 Usar la directiva de plantilla controlar la presentación de información en la ventana de **Propiedades** es diferente de implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> controla las propiedades de objeto en el nivel de componente, mientras que la directiva de plantilla se puede utilizar para restringir las propiedades de objeto de la solución o el proyecto.  en otras palabras  
  
-   Implemente los métodos en <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> para determinar lo que se muestra en la ventana de **Propiedades** para objetos específicos  
  
-   Utilice la directiva de plantilla en la solución y proyecto para determinar lo que se muestra en la ventana de **Propiedades** para objetos previamente especificados  
  
 Usar la directiva de plantilla restringir selectivamente propiedades específicas en la ventana de **Propiedades** cuando un elemento de un tipo especificado está seleccionado en **Explorador de soluciones** puede ser beneficioso a todos los miembros del equipo de desarrollo que funciona en un proyecto.  Por ejemplo, mediante la directiva de plantilla, puede configurar toda la información de la cadena de conexión de una base de datos para los desarrolladores y crear readonly de la cadena de conexión.  De esta manera, puede proporcionar una manera simple de garantizar que cada desarrollador usa la ruta de acceso correcta para el acceso a datos.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Extender propiedades](../../extensibility/internals/extending-properties.md)