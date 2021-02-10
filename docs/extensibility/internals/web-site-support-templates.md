---
title: Plantillas de soporte del sitio web | Microsoft Docs
description: Obtenga información sobre las plantillas de soporte técnico del sitio Web. Las plantillas de proyecto y elemento de sitio web de Visual Studio proporcionan códigos auxiliares de elemento y proyecto de sitio web reutilizable y personalizable.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 988b81e72ff7714cb8a0983655de551b54c9150c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940038"
---
# <a name="web-site-support-templates"></a>Plantillas de compatibilidad del sitio web
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Las plantillas de elementos y proyectos de sitio web proporcionan códigos auxiliares reutilizables y personalizables de los elementos y del proyecto de sitio web que aceleran el proceso de desarrollo mediante la eliminación de la necesidad de crear nuevos proyectos y elementos de sitios web desde cero. Para obtener más información sobre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] las plantillas, vea [crear plantillas de proyecto y de elemento](../../ide/creating-project-and-item-templates.md).

## <a name="project-template-folder"></a>Carpeta de plantillas de proyecto
 Las plantillas de proyecto web se instalan normalmente en [*ruta de instalación de Visual Studio*] \Common7\IDE\ProjectTemplates\Web \\ , cada una en una subcarpeta con el nombre del lenguaje de programación web.

## <a name="project-file"></a>Archivo de proyecto
 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno de desarrollo integrado (IDE) requiere una extensión de archivo de proyecto como una manera de asignar una plantilla al tipo de proyecto correcto. Dado que los proyectos web no tienen un archivo de proyecto, la extensión de archivo de proyecto ficticio. webproj vacío se registra para asignar la plantilla al tipo de proyecto.

 Opcionalmente, se puede Agregar una cadena de nombre de lenguaje a la plantilla para permitir que el sistema del proyecto web establezca el idioma predeterminado en el cuadro de diálogo **Agregar nuevo elemento** para los elementos basados en la plantilla. La cadena debe ser la primera línea del archivo. Debe coincidir con el nombre registrado en AddItemLanguageName en el registro del motor de IntelliSense y el nombre registrado en subtipo de proyecto (VsTemplate). Para obtener más información, vea [atributos de compatibilidad del sitio web](../../extensibility/internals/web-site-support-attributes.md).

 Si la cadena no está presente, el sistema del proyecto web intenta determinar el idioma predeterminado en función del atributo de idioma y de las extensiones de archivo de las páginas agregadas al proyecto web por la plantilla de proyecto.

## <a name="project-templates"></a>Plantillas de proyecto
 Las plantillas de proyecto de sitio web se usan para crear nuevos sitios web como respuesta al comando **nuevo sitio web** en el menú **archivo** . Actualmente se admiten tres tipos de proyecto de sitio web:

- Proyectos de sitio web vacíos

- Proyectos de sitios web

- Proyectos de servicio Web

### <a name="empty-web-site-projects"></a>Proyectos de sitio web vacíos
 Estos archivos crean un nuevo sitio Web vacío como respuesta al comando **sitio Web vacío** , que está disponible después de elegir **archivo**  >  **nuevo sitio web**:

- EmptyWeb. vstemplate

     El archivo de plantilla que guía la creación del nuevo sitio Web vacío.

- EmptyWeb. webproj vacío

     Este archivo es un artefacto del sistema de plantillas de proyecto. Satisface la referencia del archivo de proyecto en el archivo EmptyWeb. vstemplate.

### <a name="web-site-projects"></a>Proyectos de sitios web
 Estos archivos crean un nuevo sitio web en respuesta al comando del **sitio web de ASP.net** , que está disponible después de elegir **archivo**  >  **nuevo sitio web**:

- Default.aspx

     La Página principal predeterminada del nuevo sitio Web. El atributo Language especifica el lenguaje Codebehind y el atributo Codefile especifica el archivo dependiente que contiene el código de Codebehind asociado a esta página.

- Default. aspx. *extensión* de

     El archivo dependiente que contiene el código Codebehind de la Página principal predeterminada. El lenguaje Codebehind determina la *extensión* de este archivo.

- web.config

     El archivo de configuración Web. site raíz.

- WebApplication. vstemplate

     El archivo de plantilla que determina el contenido de la solución de sitio web y fuerza la creación de la carpeta App_Data.

- WebApplication. webproj vacío

     Este archivo es un artefacto del sistema de plantillas de proyecto. Satisface la referencia del archivo de proyecto en el archivo WebApplication. vstemplate.

### <a name="web-service-projects"></a>Proyectos de servicio Web
 Estos archivos crean un nuevo sitio web en respuesta al comando del **servicio Web ASP.net** , que está disponible después de elegir **archivo**  >  **nuevo sitio web**:

- Service. asmx

     Página HTML del nuevo servicio Web. El atributo Language especifica el lenguaje Codebehind y el atributo CodeBehind especifica el archivo dependiente que contiene el código de Codebehind asociado a este servicio.

- Servicio. *extension*

     El archivo dependiente que implementa la clase de servicio. El lenguaje Codebehind determina la *extensión* de este archivo.

- web.config

- El archivo de configuración Web. site raíz.

- WebService. vstemplate

     El archivo de plantilla que determina el contenido de la solución de sitio web y fuerza la creación de las carpetas App_Data y App_Code. El servicio. el archivo de *extensión* se copia en la carpeta App_Code.

- WebService. webproj vacío

     Este archivo es un artefacto del sistema de plantillas de proyecto. Satisface la referencia del archivo de proyecto en el archivo WebService. vstemplate.

## <a name="project-item-template-folder"></a>Carpeta de plantillas de elementos de proyecto
 Proyecto web: las plantillas de elementos se instalan normalmente en [*ruta de instalación de Visual Studio*] \Common7\IDE\ItemTemplates\Web \\ , cada una en una subcarpeta con el nombre de su lenguaje de programación web.

## <a name="project-item-templates"></a>Plantillas de elementos de proyecto
 Las plantillas de elemento de proyecto de sitio web se usan para agregar nuevas páginas web a un sitio web en respuesta al comando **Agregar elemento existente** . Actualmente se admiten estos tipos de páginas web:

- Nueva clase

- Nueva página HTML

- Nuevo formulario Web Forms

- Nueva página maestra

### <a name="new-class"></a>Nueva clase
 Esta plantilla crea un nuevo archivo de código fuente que define una clase vacía como respuesta al comando **Agregar nueva clase** .

- Clase. *extension*

     El archivo de código fuente que implementa la clase vacía. El lenguaje Codebehind determina la *extensión* de este archivo.

- Clase. vstemplate

     El archivo de plantilla que crea el archivo de código fuente y determina su contenido.

### <a name="new-html-page"></a>Nueva página HTML
 Esta plantilla crea una nueva página web como respuesta al comando **Agregar nueva página HTML** .

- HTMLPage.htm

     El contenido inicial de la Página Web. Normalmente, esta página web no tiene ningún archivo dependiente de código subyacente asociado. Para crear una página inteligente con un archivo de código subyacente asociado, use la plantilla de formulario web en su lugar.

- La. vstemplate

     El archivo de plantilla que crea la página web y determina su contenido.

### <a name="new-webform"></a>Nuevo WebForm
 Esta plantilla crea una nueva página web inteligente como respuesta al comando **Agregar nuevo formulario Web Forms** .

 Para crear un archivo de origen de código subyacente dependiente, seleccione **colocar código en un archivo independiente**. De lo contrario, se crea una sola página web que tiene un bloque de scripting vacío y ninguna \<% Page %> Directiva para enlazar un archivo dependiente.

 Para crear una página de contenido para una página maestra seleccionada, seleccione **seleccionar página maestra**.

- WebForm. aspx

     El contenido inicial de la Página Web. Esta página web no tiene asociado ningún archivo dependiente de código subyacente.

- WebForm_cb. aspx

     El contenido inicial de la Página Web. Esta página web tiene asociado un archivo dependiente de Codebehind.

- Código. *extension*

     El archivo dependiente que implementa la clase WebForm. El lenguaje Codebehind determina la *extensión* de este archivo.

- ContentPage. aspx

     El contenido inicial de la página web como una página de contenido. Esta página web no tiene asociado ningún archivo dependiente de código subyacente.

- ContentPage_cb. aspx

     El contenido inicial de la página web como una página de contenido. Esta página web tiene asociado un archivo dependiente de Codebehind.

- WebForm. vstemplate

     El archivo de plantilla que determina el contenido de la nueva página web y su archivo dependiente, si existe.

### <a name="new-master-page"></a>Nueva página maestra
 Esta plantilla crea una nueva página maestra como respuesta al comando **Agregar nueva página maestra** .

 Para crear un archivo de origen de código subyacente dependiente, seleccione **colocar código en un archivo independiente**. De lo contrario, se crea una sola página web que tiene un bloque de scripting vacío y ninguna \<% Page %> Directiva para enlazar un archivo dependiente.

- MasterPage. Master

     El contenido inicial de la página maestra. Esta página maestra no tiene asociado ningún archivo dependiente de código subyacente.

- MasterPage_cb. Master

     El contenido inicial de la página maestra. Esta página maestra tiene asociado un archivo dependiente de Codebehind.

- Código. *extensión* de

     El archivo dependiente que implementa la clase de página maestra. El lenguaje Codebehind determina la *extensión* de este archivo.

- MasterPage. vstemplate

     El archivo de plantilla que determina el contenido de la nueva página maestra y su archivo dependiente, si existe.

## <a name="see-also"></a>Vea también
- [Compatibilidad del sitio web](../../extensibility/internals/web-site-support.md)
