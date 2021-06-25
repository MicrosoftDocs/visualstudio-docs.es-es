---
title: Plantillas de soporte técnico de sitio web | Microsoft Docs
description: Obtenga información sobre las plantillas de soporte técnico de sitios web. Visual Studio proyecto de sitio web y plantillas de elemento proporcionan código auxiliar de elemento y proyecto de sitio web reutilizables y personalizables.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a1bd391d13a6d650cb4d23ce78789a66ef50c2e3
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898904"
---
# <a name="web-site-support-templates"></a>Plantillas de compatibilidad del sitio web
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Las plantillas de elemento y proyecto de sitio web proporcionan código auxiliar de elemento y proyecto de sitio web reutilizables y personalizables que aceleran el proceso de desarrollo mediante la eliminación de la necesidad de crear nuevos proyectos y elementos de sitio web desde cero. Para obtener más información sobre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] las plantillas, vea [Creating Project and Item Templates](../../ide/creating-project-and-item-templates.md).

## <a name="project-template-folder"></a>Carpeta de plantilla de proyecto
 Las plantillas de proyecto web se suelen instalar en [ ruta de instalación de *Visual Studio*]\Common7\IDE\ProjectTemplates\Web , cada una de ellas en una subcarpeta con el nombre del lenguaje de programación \\ web.

## <a name="project-file"></a>Archivo de proyecto
 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno de desarrollo integrado (IDE) requiere una extensión de archivo de proyecto como una manera de asignar una plantilla al tipo de proyecto correcto. Dado que los proyectos web no tienen un archivo de proyecto, la extensión de archivo de proyecto ficticio .webproj se registra para asignar la plantilla al tipo de proyecto.

 Opcionalmente, se puede agregar una cadena de nombre de idioma a la plantilla  para permitir que el sistema de proyectos web establezca el idioma predeterminado en el cuadro de diálogo Agregar nuevo elemento para los elementos basados en la plantilla. La cadena debe ser la primera línea del archivo. Debe coincidir con el nombre registrado en AddItemLanguageName en el registro del motor de IntelliSense y con el nombre registrado en Project Subtype(VsTemplate). Para obtener más información, vea [Atributos de compatibilidad de sitios web](../../extensibility/internals/web-site-support-attributes.md).

 Si la cadena no está presente, el sistema de proyectos web intenta determinar el idioma predeterminado en función del atributo Language y las extensiones de archivo de las páginas agregadas al proyecto web por la plantilla de proyecto.

## <a name="project-templates"></a>Plantillas de proyecto
 Las plantillas de proyecto de sitio web se usan para compilar nuevos sitios web en respuesta al **comando Nuevo** sitio web en el **menú** Archivo . Actualmente se admiten tres tipos de proyecto de sitio web:

- Proyectos de sitio web vacíos

- Proyectos de sitio web

- Proyectos de servicio web

### <a name="empty-web-site-projects"></a>Proyectos de sitio web vacíos
 Estos archivos crean un nuevo sitio web vacío en respuesta al comando **Sitio web** vacío, que está disponible después de elegir **Archivo** nuevo  >  **sitio web**:

- EmptyWeb.vstemplate

     Archivo de plantilla que guía la creación del nuevo sitio web vacío.

- EmptyWeb.webproj

     Este archivo es un artefacto del sistema de plantillas de proyecto. Satisface la referencia del archivo de proyecto en el archivo EmptyWeb.vstemplate.

### <a name="web-site-projects"></a>Proyectos de sitio web
 Estos archivos crean un nuevo sitio web en respuesta al comando **ASP.NET Sitio web,** que está disponible después de elegir **Archivo** nuevo  >  **sitio web**:

- Default.aspx

     Página principal predeterminada del nuevo sitio web. El atributo Language especifica el lenguaje codebehind y el atributo CodeFile especifica el archivo dependiente que contiene el código codebehind asociado a esta página.

- Default.aspx. *extensión*

     Archivo dependiente que contiene el código de la página principal predeterminada. El lenguaje codebehind determina la *extensión* de este archivo.

- web.config

     Archivo de configuración web.site raíz.

- WebApplication.vstemplate

     Archivo de plantilla que determina el contenido de la solución de sitio web y fuerza la creación de la App_Data carpeta.

- WebApplication.webproj

     Este archivo es un artefacto del sistema de plantillas de proyecto. Satisface la referencia del archivo de proyecto en el archivo WebApplication.vstemplate.

### <a name="web-service-projects"></a>Proyectos de servicio web
 Estos archivos crean un nuevo sitio web en respuesta al comando **ASP.NET Web Service,** que está disponible después de elegir **Archivo** nuevo  >  **sitio web**:

- Service.asmx

     Página HTML del nuevo servicio web. El atributo Language especifica el lenguaje codebehind y el atributo CodeBehind especifica el archivo dependiente que contiene el código codebehind asociado a este servicio.

- Servicio. *extension*

     Archivo dependiente que implementa la clase de servicio. El lenguaje codebehind determina la *extensión* de este archivo.

- web.config

- Archivo de configuración web.site raíz.

- WebService.vstemplate

     Archivo de plantilla que determina el contenido de la solución de sitio web y fuerza la creación de App_Data y App_Code carpetas. El servicio. *El* archivo de extensión se copia en la carpeta App_Code extensión.

- WebService.webproj

     Este archivo es un artefacto del sistema de plantillas de proyecto. Satisface la referencia del archivo de proyecto en el archivo WebService.vstemplate.

## <a name="project-item-template-folder"></a>Carpeta de plantilla de elemento de proyecto
 Las plantillas de elemento de proyecto web normalmente se instalan en [ ruta de instalación de *Visual Studio*]\Common7\IDE\ItemTemplates\Web , cada una de ellas en una subcarpeta con el nombre de su lenguaje de programación \\ web.

## <a name="project-item-templates"></a>Plantillas de elementos de proyecto
 Las plantillas de elemento de proyecto de sitio web se usan para agregar nuevas páginas web a un sitio web en respuesta al **comando Agregar elemento** existente. Actualmente se admiten estos tipos de páginas web:

- Nueva clase

- Nueva página HTML

- Nuevo formulario web

- Nueva página maestra

### <a name="new-class"></a>Nueva clase
 Esta plantilla crea un nuevo archivo de código fuente que define una clase vacía en respuesta al **comando Agregar nueva** clase.

- Clase. *extension*

     Archivo de código fuente que implementa la clase vacía. El lenguaje codebehind determina la *extensión* de este archivo.

- Class.vstemplate

     Archivo de plantilla que crea el archivo de origen y determina su contenido.

### <a name="new-html-page"></a>Nueva página HTML
 Esta plantilla crea una nueva página web en respuesta al **comando Agregar nueva página HTML.**

- HTMLPage.htm

     Contenido inicial de la página web. Esta página web normalmente no tiene ningún archivo dependiente de codebehind asociado. Para crear una página inteligente con un archivo codebehind asociado, use en su lugar la plantilla formulario web.

- HTMLPage.vstemplate

     Archivo de plantilla que crea la página web y determina su contenido.

### <a name="new-webform"></a>Nuevo WebForm
 Esta plantilla crea una nueva página web inteligente en respuesta al **comando Agregar nuevo formulario** web.

 Para crear un archivo de código fuente dependiente, seleccione **Colocar código en un archivo independiente.** De lo contrario, se crea una sola página web que tiene un bloque de scripting vacío y ninguna directiva para enlazar \<% Page %> un archivo dependiente.

 Para crear una página de contenido para una página maestra seleccionada, seleccione **Seleccionar página maestra**.

- WebForm.aspx

     Contenido inicial de la página web. Esta página web no tiene ningún archivo dependiente de codebehind asociado.

- WebForm_cb.aspx

     Contenido inicial de la página web. Esta página web tiene un archivo dependiente de codebehind asociado.

- Codebehind. *extension*

     Archivo dependiente que implementa la clase webform. El lenguaje codebehind determina la *extensión* de este archivo.

- ContentPage.aspx

     El contenido inicial de la página web como una página de contenido. Esta página web no tiene ningún archivo dependiente de codebehind asociado.

- ContentPage_cb.aspx

     El contenido inicial de la página web como una página de contenido. Esta página web tiene un archivo dependiente de codebehind asociado.

- WebForm.vstemplate

     Archivo de plantilla que determina el contenido de la nueva página web y su archivo dependiente, si lo hay.

### <a name="new-master-page"></a>Nueva página maestra
 Esta plantilla crea una nueva página maestra en respuesta al **comando Agregar nueva página** maestra.

 Para crear un archivo de código fuente dependiente, seleccione **Colocar código en un archivo independiente.** De lo contrario, se crea una sola página web que tiene un bloque de scripting vacío y ninguna directiva para enlazar \<% Page %> un archivo dependiente.

- MasterPage.master

     Contenido inicial de la página maestra. Esta página maestra no tiene ningún archivo dependiente de codebehind asociado.

- MasterPage_cb.master

     Contenido inicial de la página maestra. Esta página maestra tiene un archivo dependiente de codebehind asociado.

- Codebehind. *extensión*

     Archivo dependiente que implementa la clase de página maestra. El lenguaje codebehind determina la *extensión* de este archivo.

- MasterPage.vstemplate

     Archivo de plantilla que determina el contenido de la nueva página maestra y su archivo dependiente, si lo hay.

## <a name="see-also"></a>Consulta también
- [Compatibilidad del sitio web](../../extensibility/internals/web-site-support.md)
