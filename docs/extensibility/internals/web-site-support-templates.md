---
title: "Plantillas de soporte técnico del sitio Web | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c4e3d64f77064c04e131853786495c921711f2d0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="web-site-support-templates"></a>Plantillas de soporte técnico del sitio Web
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Plantillas de proyecto y elemento de sitio Web proporcionan sitio Web reutilizables y personalizables proyecto y elemento códigos auxiliares que aceleran el proceso de desarrollo mediante la eliminación de la necesidad de crear nuevos proyectos de sitios Web y los elementos desde el principio. Para obtener más información sobre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] plantillas, consulte [crear plantillas de proyecto y elemento](../../ide/creating-project-and-item-templates.md).  
  
## <a name="project-template-folder"></a>Carpeta de plantillas de proyecto  
 Plantillas de plantilla de proyecto Web normalmente se instalan en [*ruta de acceso de instalación de Visual Studio*] \Common7\IDE\ProjectTemplates\Web\\, cada una en una subcarpeta que se denomina con el lenguaje de programación web.  
  
## <a name="project-file"></a>Archivo de proyecto  
 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE) requiere una extensión de archivo de proyecto como un método para asignar una plantilla para el tipo de proyecto correcto. Dado que los proyectos Web no tiene un archivo de proyecto, el .webproj de extensión de archivo de proyecto ficticio está registrado para admitir esto.  
  
 Si lo desea, una cadena de nombre de idioma puede agregarse a la plantilla para habilitar el sistema del proyecto Web establecer el idioma predeterminado en el **Agregar nuevo elemento** cuadro de diálogo para los elementos basados en la plantilla. La cadena debe ser la primera línea del archivo y debe coincidir con el nombre registrado en AddItemLanguageName en el registro del motor de Intellisense y el nombre registrado en el proyecto Subtype(VsTemplate). Para obtener más información, consulte [sitio Web de soporte técnico de atributos](../../extensibility/internals/web-site-support-attributes.md).  
  
 Si la cadena no está presente, el sistema del proyecto Web intentará determinar el idioma predeterminado en función de las extensiones de atributo y el archivo de lenguaje de las páginas que se agregan al proyecto Web mediante la plantilla de proyecto.  
  
## <a name="project-templates"></a>Plantillas de proyecto  
 Plantillas de proyecto de sitio Web se utilizan para crear nuevos sitios Web en respuesta a la **nuevo sitio Web** comando el **archivo** menú. Actualmente se admiten tres tipos de proyectos de sitio Web:  
  
-   Proyectos de sitio Web vacío  
  
-   Proyectos de sitios Web  
  
-   Proyectos de servicio Web  
  
### <a name="empty-web-site-projects"></a>Proyectos de sitio Web vacío  
 Estos archivos crear un nuevo sitio Web vacío en respuesta a la **sitio Web vacío** comando, que está disponible después de seleccionar **nuevo sitio Web** en el **archivo** menú:  
  
-   EmptyWeb.vstemplate  
  
     El archivo de plantilla que le guía a la creación del nuevo sitio Web vacío.  
  
-   EmptyWeb.webproj  
  
     Este archivo es un artefacto de sistema de la plantilla de proyecto. Satisface la referencia del archivo de proyecto en el archivo EmptyWeb.vstemplate.  
  
### <a name="web-site-projects"></a>Proyectos de sitios Web  
 Estos archivos crear un nuevo sitio Web en respuesta a la **sitio Web de ASP.NET** comando, que está disponible después de seleccionar **nuevo sitio Web** en el **archivo** menú:  
  
-   Default.aspx  
  
     La página principal predeterminada para el nuevo sitio Web. El atributo Language especifica el lenguaje de código subyacente y el atributo CodeFile especifica el archivo dependiente que contiene el código de código subyacente asociado a esta página.  
  
-   Default.aspx. *extensión*  
  
     El archivo dependiente que contiene el código de código subyacente para la página principal predeterminada. El lenguaje de código subyacente determina la *extensión* de este archivo.  
  
-   web.config  
  
     El archivo de configuración de web.site de raíz.  
  
-   WebApplication.vstemplate  
  
     El archivo de plantilla que determina el contenido de la solución de sitio Web y fuerza la creación de la carpeta App_Data.  
  
-   WebApplication.webproj  
  
     Este archivo es un artefacto de sistema de la plantilla de proyecto. Satisface la referencia del archivo de proyecto en el archivo WebApplication.vstemplate.  
  
### <a name="web-service-projects"></a>Proyectos de servicio Web  
 Estos archivos crear un nuevo sitio Web en respuesta a la **servicio Web ASP.NET** comando que está disponible después de seleccionar **nuevo sitio Web** en el **archivo** menú:  
  
-   Service.asmx  
  
     La página HTML para el nuevo servicio Web. El atributo Language especifica el lenguaje de código subyacente y el atributo de código subyacente especifica el archivo dependiente que contiene el código de código subyacente asociado a este servicio.  
  
-   Servicio. *extensión*  
  
     El archivo dependiente que implementa la clase de servicio. El lenguaje de código subyacente determina la *extensión* de este archivo.  
  
-   web.config  
  
-   El archivo de configuración de web.site de raíz.  
  
-   WebService.vstemplate  
  
     El archivo de plantilla que determina el contenido de la solución de sitio Web y fuerza la creación de las carpetas App_Data y App_Code. El servicio. *extensión* archivo se copia en la carpeta App_Code.  
  
-   WebService.webproj  
  
     Este archivo es un artefacto de sistema de la plantilla de proyecto. Satisface la referencia del archivo de proyecto en el archivo WebService.vstemplate.  
  
## <a name="project-item-template-folder"></a>Carpeta de plantillas de elemento de proyecto  
 Plantillas de plantilla de elemento de proyecto Web normalmente se instalan en [*ruta de acceso de instalación de Visual Studio*] \Common7\IDE\ItemTemplates\Web\\, cada una en una subcarpeta denominada después de su lenguaje de programación web.  
  
## <a name="project-item-templates"></a>Plantillas de elementos de proyecto  
 Plantillas de elementos de proyecto de sitio Web se usan para agregar nuevas páginas Web en un sitio Web en respuesta a la **Agregar elemento existente** comando. Actualmente se admiten estos tipos de páginas Web:  
  
-   Nueva clase  
  
-   Nueva página HTML  
  
-   Nuevo formulario Web Forms  
  
-   Nueva página maestra  
  
### <a name="new-class"></a>Nueva clase  
 Esta plantilla crea un nuevo archivo de origen que define una clase vacía en respuesta a la **agregar nueva clase** comando.  
  
-   Clase. *extensión*  
  
     El archivo de origen que implementa la clase vacía. El lenguaje de código subyacente determina la *extensión* de este archivo.  
  
-   Class.vstemplate  
  
     El archivo de plantilla que crea el archivo de origen y determina su contenido.  
  
### <a name="new-html-page"></a>Nueva página HTML  
 Esta plantilla crea una nueva página Web en respuesta a la **agregar nueva página HTML** comando.  
  
-   HTMLPage.htm  
  
     El contenido inicial de la página Web. Normalmente, esta página Web no tiene ningún archivo dependiente de código subyacente asociado. Para crear una página inteligente con un archivo de código subyacente asociados, use la plantilla de formulario Web Forms en su lugar.  
  
-   HTMLPage.vstemplate  
  
     El archivo de plantilla que crea la página Web y determina su contenido.  
  
### <a name="new-webform"></a>WebForm nueva  
 Esta plantilla crea una nueva página Web inteligente en respuesta a la **Agregar nuevo formulario Web Forms** comando.  
  
 Para crear un archivo de código fuente dependiente de código subyacente, seleccione **colocar código en un archivo independiente**. En caso contrario, se crea una única página Web que tiene un bloque de secuencias de comandos vacío y no \<% Page % > directivas para enlazar un archivo dependiente.  
  
 Para crear una página de contenido de una página maestra seleccionada, seleccione **seleccionar la página principal**.  
  
-   WebForm.aspx  
  
     El contenido inicial de la página Web. Esta página Web no tiene ningún archivo dependiente de código subyacente asociado.  
  
-   WebForm_cb.aspx  
  
     El contenido inicial de la página Web. Esta página Web tiene un archivo dependiente de código subyacente asociado.  
  
-   Código subyacente. *extensión*  
  
     El archivo dependiente que implementa la clase de formulario Web Forms. El lenguaje de código subyacente determina la *extensión* de este archivo.  
  
-   ContentPage.aspx  
  
     El contenido inicial de la página Web como una página de contenido. Esta página Web no tiene ningún archivo dependiente de código subyacente asociado.  
  
-   ContentPage_cb.aspx  
  
     El contenido inicial de la página Web como una página de contenido. Esta página Web tiene un archivo dependiente de código subyacente asociado.  
  
-   WebForm.vstemplate  
  
     El archivo de plantilla que determina el contenido de la nueva página web y sus archivos dependientes, si los hay.  
  
### <a name="new-master-page"></a>Nueva página principal  
 Esta plantilla crea una nueva página maestra en respuesta a la **agregar nueva página maestra** comando.  
  
 Para crear un archivo de código fuente dependiente de código subyacente, seleccione **colocar código en un archivo independiente**. En caso contrario, se crea una única página Web que tiene un bloque de secuencias de comandos vacío y no \<% Page % > directivas para enlazar un archivo dependiente.  
  
-   MasterPage.master  
  
     El contenido inicial de la página maestra. Esta página principal no tiene ningún archivo dependiente de código subyacente asociado.  
  
-   MasterPage_cb.master  
  
     El contenido inicial de la página maestra. Esta página principal tiene un archivo dependiente de código subyacente asociado.  
  
-   Código subyacente. *extensión*  
  
     El archivo dependiente que implementa la clase de página maestra. El lenguaje de código subyacente determina la *extensión* de este archivo.  
  
-   MasterPage.vstemplate  
  
     El archivo de plantilla que determina el contenido de la nueva página maestra y sus archivos dependientes, si los hay.  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con sitios web](../../extensibility/internals/web-site-support.md)