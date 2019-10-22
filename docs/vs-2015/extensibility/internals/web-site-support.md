---
title: Compatibilidad con sitios Web | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f1a96504783de466551c6fb9d055b95ba38df760
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687688"
---
# <a name="web-site-support"></a>Compatibilidad del sitio web
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un sistema de proyectos de sitio Web es un sistema de proyecto que crea proyectos Web. Los proyectos Web a su vez crean aplicaciones Web. Un proyecto de sitio Web genera un archivo ejecutable para cada página Web que está asociado el código. Se generan archivos ejecutables adicionales de los archivos de código fuente en la carpeta /bin.  
  
 Sistemas de proyectos de sitio Web se crean mediante la adición de plantillas y los atributos de registro en un sistema de proyecto existente. Uno de estos atributos selecciona el proveedor de IntelliSense para el lenguaje. La implementación del proveedor IntelliSense controla las referencias y llama al compilador del lenguaje cuando se solicita una página Web inteligente que no se almacena en caché.  
  
 El compilador de lenguaje que se utiliza para compilar las páginas Web debe estar registrado con [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]. Puede usar el [ \<compilador > elemento](https://msdn.microsoft.com/library/7a151659-b803-4c27-b5ce-1c4aa0d5a823) en un archivo Web.config para registrar el compilador, como en el ejemplo siguiente:  
  
```  
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>  
```  
  
## <a name="in-this-section"></a>En esta sección  
 [Plantillas de compatibilidad del sitio web](../../extensibility/internals/web-site-support-templates.md)  
 Enumera las plantillas que puede usar para crear nuevos proyectos de sitios Web y los elementos asociados.  
  
 [Atributos de compatibilidad del sitio web](../../extensibility/internals/web-site-support-attributes.md)  
 Presenta los atributos de registro que se conectan a un proyecto de sitio Web [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] y [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)].  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Proyectos web](../../extensibility/internals/web-projects.md)  
 Presenta información general de los dos tipos de proyectos Web, proyectos de sitios Web y proyectos de aplicación Web.
