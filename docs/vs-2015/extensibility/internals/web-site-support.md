---
title: Compatibilidad con sitios web | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687688"
---
# <a name="web-site-support"></a>Compatibilidad del sitio web
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un sistema de proyectos de sitio web es un sistema de proyectos que crea proyectos Web. Los proyectos web a su vez crean aplicaciones Web. Un proyecto de sitio web genera un archivo ejecutable para cada página web que tiene código asociado. Los archivos ejecutables adicionales se generan a partir de los archivos de código fuente en la carpeta/App_Code.  
  
 Los sistemas de proyecto de sitio web se crean mediante la adición de plantillas y atributos de registro a un sistema de proyecto existente. Uno de estos atributos selecciona el proveedor de IntelliSense para el lenguaje. La implementación del proveedor de IntelliSense controla las referencias y llama al compilador de lenguaje cuando se solicita una página web inteligente que no está almacenada en caché.  
  
 El compilador de lenguaje utilizado para compilar páginas web se debe registrar con [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] . Puede usar el [ \<compiler> elemento](https://msdn.microsoft.com/library/7a151659-b803-4c27-b5ce-1c4aa0d5a823) en un archivo de Web.config para registrar el compilador, como en el ejemplo siguiente:  
  
```  
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>  
```  
  
## <a name="in-this-section"></a>En esta sección  
 [Plantillas de compatibilidad del sitio web](../../extensibility/internals/web-site-support-templates.md)  
 Muestra las plantillas que puede usar para crear nuevos proyectos de sitios web y elementos asociados.  
  
 [Atributos de compatibilidad del sitio web](../../extensibility/internals/web-site-support-attributes.md)  
 Presenta los atributos de registro que conectan un proyecto de sitio web a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] y [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] .  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Proyectos Web](../../extensibility/internals/web-projects.md)  
 Presenta información general de los dos tipos de proyectos Web, proyectos de sitio web y proyectos de aplicación Web.
