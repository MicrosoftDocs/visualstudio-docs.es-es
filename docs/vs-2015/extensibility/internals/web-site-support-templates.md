---
title: Plantillas de sitio Web soporte técnico | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fce793b077460f2c141de0a75d612bb9254f7b3b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58999483"
---
# <a name="web-site-support-templates"></a>Plantillas de compatibilidad del sitio web
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Plantillas de proyecto y elemento de sitio Web proporcionan stubs de proyectos y elementos de sitio Web reutilizables y personalizables que aceleran el proceso de desarrollo mediante la eliminación de la necesidad de crear nuevos proyectos de sitios Web y los elementos desde el principio. Para obtener más información sobre [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] plantillas, consulte [crear plantillas de proyecto y elemento](../../ide/creating-project-and-item-templates.md).  
  
## <a name="project-template-folder"></a>Carpeta de plantillas de proyecto  
 Plantillas de plantilla de proyecto Web normalmente se instalan en [*ruta de instalación de Visual Studio*] \Common7\IDE\ProjectTemplates\Web\\, cada una en una subcarpeta que se denomina con el lenguaje de programación web.  
  
## <a name="project-file"></a>Archivo de proyecto  
 El [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] el entorno de desarrollo integrado (IDE) requiere una extensión de archivo de proyecto como una forma de asignar una plantilla para el tipo de proyecto correcta. Dado que los proyectos Web no tienen un archivo de proyecto, se registra el .webproj de extensión de archivo de proyecto ficticio para que sea compatible.  
  
 Si lo desea, una cadena de nombre de idioma puede agregarse a la plantilla para habilitar el sistema de proyecto Web establecer el idioma predeterminado en el **Agregar nuevo elemento** cuadro de diálogo para los elementos basados en la plantilla. La cadena debe ser la primera línea del archivo y debe coincidir con el nombre registrado en AddItemLanguageName en el registro del motor de Intellisense y el nombre registrado en el proyecto Subtype(VsTemplate). Para obtener más información, consulte [sitio Web de soporte técnico de atributos](../../extensibility/internals/web-site-support-attributes.md).  
  
 Si la cadena no está presente, el sistema del proyecto Web intentará determinar el idioma predeterminado en función de las extensiones de atributo y el archivo de lenguaje de las páginas que se agrega al proyecto Web mediante la plantilla de la plantilla de proyecto.  
  
## <a name="project-templates"></a>Plantillas de proyecto  
 Plantillas de proyecto de sitio Web se usan para crear nuevos sitios Web en respuesta a la **nuevo sitio Web** comando el **archivo** menú. Actualmente se admiten tres tipos de proyectos de sitio Web:  
  
-   Proyectos de sitio Web vacío  
  
-   Proyectos de sitios Web  
  
-   Proyectos de servicio Web  
  
### <a name="empty-web-site-projects"></a>Proyectos de sitio Web vacío  
 Estos archivos creación un nuevo sitio Web vacío en respuesta a la **sitio Web vacío** comando, que está disponible después de seleccionar **nuevo sitio Web** en el **archivo** menú:  
  
-   EmptyWeb.vstemplate  
  
     El archivo de plantilla que guía a la creación del nuevo sitio Web vacío.  
  
-   EmptyWeb.webproj  
  
     Este archivo es un artefacto del sistema de plantilla del proyecto. Cumple la referencia de archivo de proyecto en el archivo EmptyWeb.vstemplate.  
  
### <a name="web-site-projects"></a>Proyectos de sitios Web  
 Estos archivos creación un nuevo sitio Web en respuesta a la **sitio Web de ASP.NET** comando, que está disponible después de seleccionar **nuevo sitio Web** en el **archivo** menú:  
  
-   Default.aspx  
  
     La página principal predeterminada para el nuevo sitio Web. El atributo Language especifica el lenguaje de código subyacente y el atributo CodeFile especifica el archivo dependiente que contiene el código de código subyacente asociado a esta página.  
  
-   Default.aspx. *extensión*  
  
     El archivo dependiente que contiene el código de código subyacente para la página principal predeterminada. El lenguaje de código subyacente determina el *extensión* de este archivo.  
  
-   web.config  
  
     El archivo de configuración raíz web.site.  
  
-   WebApplication.vstemplate  
  
     El archivo de plantilla que determina el contenido de la solución del sitio Web y fuerza la creación de la carpeta App_Data.  
  
-   WebApplication.webproj  
  
     Este archivo es un artefacto del sistema de plantilla del proyecto. Cumple la referencia de archivo de proyecto en el archivo WebApplication.vstemplate.  
  
### <a name="web-service-projects"></a>Proyectos de servicio Web  
 Estos archivos creación un nuevo sitio Web en respuesta a la **servicio Web ASP.NET** comando que está disponible después de seleccionar **nuevo sitio Web** en el **archivo** menú:  
  
-   Service.asmx  
  
     La página HTML para el nuevo servicio Web. El atributo Language especifica el lenguaje de código subyacente y el atributo de código subyacente especifica el archivo dependiente que contiene el código de código subyacente asociado con este servicio.  
  
-   Servicio. *extension*  
  
     El archivo dependiente que implementa la clase de servicio. El lenguaje de código subyacente determina el *extensión* de este archivo.  
  
-   web.config  
  
-   El archivo de configuración raíz web.site.  
  
-   WebService.vstemplate  
  
     El archivo de plantilla que determina el contenido de la solución del sitio Web y fuerza la creación de las carpetas App_Data y App_Code. El servicio. *extensión* archivo se copia en la carpeta App_Code.  
  
-   WebService.webproj  
  
     Este archivo es un artefacto del sistema de plantilla del proyecto. Cumple la referencia de archivo de proyecto en el archivo WebService.vstemplate.  
  
## <a name="project-item-template-folder"></a>Carpeta de plantillas de elemento de proyecto  
 Plantillas de plantilla de elemento de proyecto Web normalmente se instalan en [*ruta de instalación de Visual Studio*] \Common7\IDE\ItemTemplates\Web\\, cada una en una subcarpeta denominada después de su lenguaje de programación de web.  
  
## <a name="project-item-templates"></a>Plantillas de elementos de proyecto  
 Plantillas de elemento de proyecto de sitio Web se usan para agregar nuevas páginas Web en un sitio Web en respuesta a la **Agregar elemento existente** comando. Actualmente se admiten estos tipos de páginas Web:  
  
-   Nueva clase  
  
-   Nueva página HTML  
  
-   Formulario Web nuevo  
  
-   Nueva página principal  
  
### <a name="new-class"></a>Nueva clase  
 Esta plantilla crea un nuevo archivo de origen que define una clase vacía en respuesta a la **agregar nueva clase** comando.  
  
-   Clase. *extension*  
  
     El archivo de código fuente que implementa la clase vacía. El lenguaje de código subyacente determina el *extensión* de este archivo.  
  
-   Class.vstemplate  
  
     El archivo de plantilla que crea el archivo de origen y determina su contenido.  
  
### <a name="new-html-page"></a>Nueva página HTML  
 Esta plantilla crea una nueva página Web en respuesta a la **agregar nueva página HTML** comando.  
  
-   HTMLPage.htm  
  
     El contenido inicial de la página Web. Normalmente, esta página Web no tiene ningún archivo de código subyacente asociado dependientes. Para crear una página inteligente con un archivo de código subyacente asociado, use la plantilla de formulario Web Forms en su lugar.  
  
-   HTMLPage.vstemplate  
  
     El archivo de plantilla que crea la página Web y determina su contenido.  
  
### <a name="new-webform"></a>Formulario Web nuevo  
 Esta plantilla crea una nueva página Web inteligente en respuesta a la **Agregar nuevo formulario Web Forms** comando.  
  
 Para crear un archivo de código fuente dependiente codebehind, seleccione **colocar código en un archivo independiente**. En caso contrario, se crea una única página Web que tiene un bloque de secuencias de comandos vacío y no tiene \<% Page % > directivas para enlazar un archivo dependiente.  
  
 Para crear una página de contenido de una página maestra seleccionada, seleccione **seleccionar la página maestra**.  
  
-   WebForm.aspx  
  
     El contenido inicial de la página Web. Esta página Web no tiene ningún archivo de código subyacente asociado dependientes.  
  
-   WebForm_cb.aspx  
  
     El contenido inicial de la página Web. Esta página Web tiene un archivo de código subyacente asociado dependientes.  
  
-   Código subyacente. *extension*  
  
     El archivo dependiente que implementa la clase de formularios Web Forms. El lenguaje de código subyacente determina el *extensión* de este archivo.  
  
-   ContentPage.aspx  
  
     El contenido inicial de la página Web como una página de contenido. Esta página Web no tiene ningún archivo de código subyacente asociado dependientes.  
  
-   ContentPage_cb.aspx  
  
     El contenido inicial de la página Web como una página de contenido. Esta página Web tiene un archivo de código subyacente asociado dependientes.  
  
-   WebForm.vstemplate  
  
     El archivo de plantilla que determina el contenido de la nueva página web y su archivo dependiente, si existe.  
  
### <a name="new-master-page"></a>Nueva página principal  
 Esta plantilla crea una nueva página principal en respuesta a la **agregar nueva página principal** comando.  
  
 Para crear un archivo de código fuente dependiente codebehind, seleccione **colocar código en un archivo independiente**. En caso contrario, se crea una única página Web que tiene un bloque de secuencias de comandos vacío y no tiene \<% Page % > directivas para enlazar un archivo dependiente.  
  
-   MasterPage.master  
  
     El contenido inicial de la página maestra. Esta página principal no tiene ningún archivo de código subyacente asociado dependientes.  
  
-   MasterPage_cb.master  
  
     El contenido inicial de la página maestra. Esta página principal tiene un archivo de código subyacente asociado dependientes.  
  
-   Código subyacente. *extensión*  
  
     El archivo dependiente que implementa la clase de página maestra. El lenguaje de código subyacente determina el *extensión* de este archivo.  
  
-   MasterPage.vstemplate  
  
     El archivo de plantilla que determina el contenido de la nueva página principal y su archivo dependiente, si existe.  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con sitios web](../../extensibility/internals/web-site-support.md)
