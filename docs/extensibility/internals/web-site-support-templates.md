---
title: Plantillas de soporte de sitios web ( Web Site Support Templates) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e3c139ae6f2f9ec618e6382a1551a9e35eee7ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703455"
---
# <a name="web-site-support-templates"></a>Plantillas de compatibilidad del sitio web
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Las plantillas de proyecto y elemento de sitio web proporcionan códigos auxiliares de elementos y proyectos de sitio web reutilizables y personalizables que aceleran el proceso de desarrollo eliminando la necesidad de crear nuevos proyectos y elementos de sitio web desde cero. Para obtener [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] más información sobre las plantillas, vea Crear plantillas de [proyecto y elemento](../../ide/creating-project-and-item-templates.md).

## <a name="project-template-folder"></a>Carpeta de plantilla de proyecto
 Las plantillas de proyecto web se instalan normalmente en [ Ruta de\\instalación de Visual*Studio*], Common7, IDE, ProjectTemplates, Web, cada una en una subcarpeta que recibe el nombre del lenguaje de programación web.

## <a name="project-file"></a>Archivo de proyecto
 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno de desarrollo integrado (IDE) requiere una extensión de archivo de proyecto como una forma de asignar una plantilla al tipo de proyecto correcto. Dado que los proyectos web no tienen un archivo de proyecto, la extensión de archivo de proyecto ficticio .webproj se registra para asignar la plantilla al tipo de proyecto.

 Opcionalmente, se puede agregar una cadena de nombre de idioma a la plantilla, para permitir que el sistema de proyectos web establezca el idioma predeterminado en el cuadro de diálogo **Agregar nuevo elemento** para los elementos basados en la plantilla. La cadena debe ser la primera línea del archivo. Debe coincidir con el nombre registrado en AddItemLanguageName en el registro del motor de IntelliSense y el nombre registrado en Subtipo de proyecto (VsTemplate). Para obtener más información, consulte [Atributos](../../extensibility/internals/web-site-support-attributes.md)de compatibilidad con sitios web .

 Si la cadena no está presente, el sistema de proyectos web intenta determinar el idioma predeterminado en función del atributo Language y las extensiones de archivo de las páginas agregadas al proyecto Web por la plantilla de proyecto.

## <a name="project-templates"></a>Plantillas de proyecto
 Las plantillas de proyecto de sitio web se usan para crear nuevos sitios Web en respuesta al comando **Nuevo sitio web** del menú **Archivo.** Actualmente se admiten tres tipos de proyectos de sitio web:

- Proyectos de sitios web vacíos

- Proyectos de sitios web

- Proyectos de servicios web

### <a name="empty-web-site-projects"></a>Proyectos de sitios web vacíos
 Estos archivos crean un nuevo sitio Web vacío en respuesta al comando **Sitio Web vacío,** que está disponible después de elegir **Archivo** > **nuevo sitio Web:**

- EmptyWeb.vstemplate

     El archivo de plantilla que guía la creación del nuevo sitio Web vacío.

- EmptyWeb.webproj

     Este archivo es un artefacto del sistema de plantillas de proyecto. Satisface la referencia del archivo de proyecto en el archivo EmptyWeb.vstemplate.

### <a name="web-site-projects"></a>Proyectos de Sitios Web
 Estos archivos crean un nuevo sitio Web en respuesta al comando **ASP.NET sitio Web,** que está disponible después de elegir **Archivo** > **nuevo sitio Web:**

- Default.aspx

     La página de inicio predeterminada para el nuevo sitio Web. El language atributo especifica el lenguaje de código subyacente y el CodeFile atributo especifica el archivo dependiente que contiene el código subyacente código asociado a esta página.

- Default.aspx. *extensión*

     El archivo dependiente que contiene el código subyacente para la página principal predeterminada. El lenguaje de código subyacente determina la *extensión* de este archivo.

- web.config

     El archivo de configuración web.site raíz.

- WebApplication.vstemplate

     El archivo de plantilla que determina el contenido de la solución de sitio Web y fuerza la creación de la carpeta App_Data.

- WebApplication.webproj

     Este archivo es un artefacto del sistema de plantillas de proyecto. Satisface la referencia del archivo de proyecto en el archivo WebApplication.vstemplate.

### <a name="web-service-projects"></a>Proyectos de Servicio Web
 Estos archivos crean un nuevo sitio Web en respuesta al comando **ASP.NET servicio web,** que está disponible después de elegir **Archivo** > **nuevo sitio Web:**

- Service.asmx

     La página HTML del nuevo servicio web. El language atributo especifica el lenguaje de código subyacente y el CodeBehind atributo especifica el archivo dependiente que contiene el código subyacente código asociado a este servicio.

- Servicio. *Extensión*

     El archivo dependiente que implementa la clase de servicio. El lenguaje de código subyacente determina la *extensión* de este archivo.

- web.config

- El archivo de configuración web.site raíz.

- WebService.vstemplate

     El archivo de plantilla que determina el contenido de la solución de sitio Web y fuerza la creación de las carpetas App_Data y App_Code. El servicio. *archivo* de extensión se copia en la carpeta App_Code.

- WebService.webproj

     Este archivo es un artefacto del sistema de plantillas de proyecto. Satisface la referencia del archivo de proyecto en el archivo WebService.vstemplate.

## <a name="project-item-template-folder"></a>Carpeta de plantilla de elemento de proyecto
 Las plantillas de elemento sde proyecto web se instalan normalmente en [ Ruta\\de instalación de Visual*Studio*], Common7, IDE, ItemTemplates, Web, cada una de ellas en una subcarpeta con el nombre de su lenguaje de programación web.

## <a name="project-item-templates"></a>Plantillas de elementos de proyecto
 Las plantillas de elemento de proyecto de sitio web se usan para agregar nuevas páginas Web a un sitio Web en respuesta al comando **Agregar elemento existente.** Actualmente se admiten estos tipos de páginas Web:

- Nueva clase

- Nueva página HTML

- Nuevo formulario web

- Nueva página maestra

### <a name="new-class"></a>Nueva clase
 Esta plantilla crea un nuevo archivo de origen que define una clase vacía en respuesta al comando **Agregar nueva clase.**

- Clase. *Extensión*

     El archivo de origen que implementa la clase vacía. El lenguaje de código subyacente determina la *extensión* de este archivo.

- Class.vstemplate

     El archivo de plantilla que crea el archivo de origen y determina su contenido.

### <a name="new-html-page"></a>Nueva página HTML
 Esta plantilla crea una nueva página Web en respuesta al comando **Agregar nueva página HTML.**

- HTMLPage.htm

     El contenido inicial de la página Web. Esta página Web normalmente no tiene ningún archivo dependiente de código asociado. Para crear una página inteligente con un archivo de código subyacente asociado, utilice la plantilla de formulario web en su lugar.

- HTMLPage.vstemplate

     El archivo de plantilla que crea la página Web y determina su contenido.

### <a name="new-webform"></a>Nuevo WebForm
 Esta plantilla crea una nueva página Web inteligente en respuesta al comando **Agregar nuevo formulario web.**

 Para crear un archivo de código fuente dependiente detrás, seleccione **Colocar código en un archivo independiente.** De lo contrario, se crea una sola página \<Web que tiene un bloque de scripting vacío y no % Page %> directivas para enlazar un archivo dependiente.

 Para crear una página de contenido para una página maestra seleccionada, seleccione **Seleccionar página maestra**.

- WebForm.aspx

     El contenido inicial de la página Web. Esta página Web no tiene ningún código asociado detrás del archivo dependiente.

- WebForm_cb.aspx

     El contenido inicial de la página Web. Esta página Web tiene un archivo dependiente de código asociado.

- Codebehind. *Extensión*

     El archivo dependiente que implementa la clase de formulario web. El lenguaje de código subyacente determina la *extensión* de este archivo.

- ContentPage.aspx

     El contenido inicial de la página Web como una página de contenido. Esta página Web no tiene ningún código asociado detrás del archivo dependiente.

- ContentPage_cb.aspx

     El contenido inicial de la página Web como una página de contenido. Esta página Web tiene un archivo dependiente de código asociado.

- WebForm.vstemplate

     El archivo de plantilla que determina el contenido de la nueva página web y su archivo dependiente, si existe.

### <a name="new-master-page"></a>Nueva página maestra
 Esta plantilla crea una nueva página maestra en respuesta al comando **Agregar nueva página maestra.**

 Para crear un archivo de código fuente dependiente detrás, seleccione **Colocar código en un archivo independiente.** De lo contrario, se crea una sola \<página Web que tiene un bloque de scripting vacío y no % Page %> directivas para enlazar un archivo dependiente.

- MasterPage.master

     El contenido inicial de la página maestra. Esta página maestra no tiene ningún código asociado detrás del archivo dependiente.

- MasterPage_cb.maestro

     El contenido inicial de la página maestra. Esta página maestra tiene un archivo dependiente de código asociado.

- Codebehind. *extensión*

     El archivo dependiente que implementa la clase de página maestra. El lenguaje de código subyacente determina la *extensión* de este archivo.

- MasterPage.vstemplate

     El archivo de plantilla que determina el contenido de la nueva página maestra y su archivo dependiente, si existe.

## <a name="see-also"></a>Vea también
- [Compatibilidad del sitio web](../../extensibility/internals/web-site-support.md)
