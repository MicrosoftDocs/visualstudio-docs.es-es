---
title: Directiva de plantilla y la ventana Propiedades | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 759864533aa5bd3455a4e01c6642817107abb1a3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="template-policy-and-the-properties-window"></a>Directiva de plantilla y la ventana Propiedades
Cuando un proyecto se encuentra dentro de un proyecto de enterprise Templates, ese proyecto de enterprise Templates puede aplicar directivas. Directiva de plantilla se convierte en un sistema de restricción que puede utilizarse para establecer los valores predeterminados para las propiedades, ocultar propiedades, agregar propiedades y así sucesivamente.  
  
 Usa una directiva de plantilla para controlar la visualización de información de la **propiedades** ventana es diferente de la implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> administra las propiedades de objeto en el nivel de componente, aunque se puede utilizar la directiva de plantilla para restringir las propiedades del objeto en el nivel de solución o proyecto. En otras palabras  
  
-   Implementar los métodos en <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> para determinar lo que se muestra en el **propiedades** ventana para objetos específicos  
  
-   Usar la directiva de plantilla en el nivel de solución y proyecto para determinar lo que se muestra en el **propiedades** ventana para los objetos especificados anteriormente  
  
 Uso de directivas de plantilla para restringir de forma selectiva determinadas propiedades de la **propiedades** ventana cuando un elemento de proyecto de un tipo especificado se selecciona en **el Explorador de soluciones** puede ser beneficioso para todos los miembros de el equipo de desarrollo trabaja en un proyecto. Por ejemplo, mediante la directiva de plantilla, puede configurar toda la información de cadena de conexión en una base de datos para los desarrolladores de software y que la cadena de conexión de solo lectura. De esa manera, puede proporcionar una manera sencilla de asegurarse de que cada desarrollador usa la ruta de acceso correcta para el acceso de datos.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Extensión de propiedades](../../extensibility/internals/extending-properties.md)