---
title: Directiva de plantilla y la ventana Propiedades | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 695b65d65d03717dd2c2579584d61227ecf447cb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51767324"
---
# <a name="template-policy-and-the-properties-window"></a>Directiva de plantilla y ventana Propiedades
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cuando un proyecto se encuentra dentro de una plantilla de proyecto, esa plantilla de proyecto puede aplicar directivas. Directiva de plantilla se convierte en un sistema de restricción que se puede utilizar para establecer valores predeterminados para las propiedades, ocultar propiedades, agregar propiedades y así sucesivamente.  
  
 Mediante la directiva de plantilla para controlar la presentación de información en el **propiedades** ventana es diferente de la implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> administra las propiedades de objeto en el nivel de componente, aunque se puede usar la directiva de plantilla para restringir las propiedades del objeto en el nivel de solución o proyecto. En otras palabras  
  
- Implementar los métodos en <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> para determinar lo que se muestra en el **propiedades** ventana para objetos específicos  
  
- Usar la directiva de plantilla en el nivel de solución y proyecto para determinar lo que se muestra en el **propiedades** ventana para los objetos especificados anteriormente  
  
  Mediante la directiva de plantilla para restringir de forma selectiva las propiedades específicas en el **propiedades** ventana cuando un elemento de proyecto de un tipo especificado se selecciona en **el Explorador de soluciones** puede ser beneficioso para todos los miembros de el equipo de desarrollo trabaja en un proyecto. Por ejemplo, mediante la directiva de plantilla, puede configurar toda la información de cadena de conexión en una base de datos para los desarrolladores y que la cadena de conexión de sólo lectura. De esa manera, puede proporcionar una manera sencilla de asegurarse de que cada desarrollador usa la ruta de acceso correcta para el acceso a datos.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Extensión de propiedades](../../extensibility/internals/extending-properties.md)

