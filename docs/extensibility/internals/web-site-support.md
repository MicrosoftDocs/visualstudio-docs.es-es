---
title: Compatibilidad con sitios Web | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 636cbee868bb53be2d0ef85bd309459570eb84c0
ms.lasthandoff: 02/22/2017

---
# <a name="web-site-support"></a>Compatibilidad con sitios Web
Un sistema de proyectos de sitio Web es un sistema de proyecto que crea proyectos Web. Proyectos Web a su vez crean aplicaciones Web. Un proyecto de sitio Web genera un archivo ejecutable para cada página Web que está asociado el código. Se generan archivos ejecutables adicionales de los archivos de código fuente en la carpeta/App_Code.  
  
 Sistemas de proyectos de sitio Web se crean mediante la adición de plantillas y los atributos de registro a un proyecto existente. Uno de estos atributos selecciona el proveedor de IntelliSense para el lenguaje. La implementación del proveedor de IntelliSense administra las referencias y llama al compilador del lenguaje cuando se solicita una página Web inteligente que no se almacena en caché.  
  
 El compilador de lenguaje utilizado para compilar páginas Web debe estar registrado en [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]. Puede usar el [ \<compilador > elemento](http://msdn.microsoft.com/Library/7a151659-b803-4c27-b5ce-1c4aa0d5a823) en un archivo Web.config para registrar el compilador, como en el ejemplo siguiente:  
  
```  
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>  
```  
  
## <a name="in-this-section"></a>En esta sección  
 [Compatibilidad con plantillas de sitio Web](../../extensibility/internals/web-site-support-templates.md)  
 Enumera las plantillas que puede usar para crear nuevos proyectos de sitios Web y los elementos asociados.  
  
 [Atributos de soporte técnico del sitio Web](../../extensibility/internals/web-site-support-attributes.md)  
 Presenta los atributos de registro que se conectan a un proyecto de sitio Web [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)].  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Proyectos Web](../../extensibility/internals/web-projects.md)  
 Presenta una descripción general de los dos tipos de proyectos Web, proyectos de sitios Web y proyectos de aplicación Web.
