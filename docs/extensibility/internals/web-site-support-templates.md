---
title: "Compatibilidad con plantillas de sitio Web | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "sitio de proyectos, plantillas"
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Compatibilidad con plantillas de sitio Web
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

las plantillas de proyecto y elemento de sitio Web de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proporcionan códigos auxiliares reutilizables y personalizables de proyecto y de elementos del sitio Web que acelera el proceso de desarrollo quitando la necesidad de crear nuevos proyectos y elementos del sitio Web desde el principio.  Para obtener más información sobre las plantillas de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , vea [Crear plantillas de proyecto y de elemento personalizadas](../../ide/creating-project-and-item-templates.md).  
  
## Carpeta plantillas de proyecto  
 Las plantillas de la plantilla de proyecto web se instalan normalmente en \[*ruta de instalación de Visual Studio*\] \\Common7\\IDE\\ProjectTemplates\\Web \\, cada uno en una subcarpeta denominada después del lenguaje de programación web.  
  
## Archivo de proyecto  
 El entorno de desarrollo integrado de \(IDE\)  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] requiere una extensión de archivo del proyecto como una manera de asignar una plantilla al tipo de proyecto correcto.  Dado que los proyectos web no tienen un archivo de proyecto, la extensión de archivo .webproj ficticia de proyecto se registra para ello.  
  
 Opcionalmente, una cadena de nombre de idioma se puede agregar a la plantilla para permitir que el sistema de proyectos web para establecer el valor predeterminado del lenguaje en el cuadro de diálogo de **Agregar nuevo elemento** para elementos basándose en la plantilla.  La cadena debe ser la primera línea del archivo y debe coincidir con el nombre registrado en AddItemLanguageName en el registro de motor Intellisense y el nombre registrado en el proyecto Subtype \(VsTemplate\).  Para obtener más información, vea [Atributos de soporte técnico del sitio Web](../../extensibility/internals/web-site-support-attributes.md).  
  
 Si la cadena no está presente, el sistema de proyectos web intentará determinar el idioma predeterminado basado en el atributo de lenguaje y extensiones de archivo de páginas agregadas al proyecto web por la plantilla de la plantilla de proyecto.  
  
## Plantillas de proyecto  
 Las plantillas de proyecto de sitio Web se utilizan para compilar nuevos sitios Web en respuesta al comando de **Nuevo sitio web** en el menú de **Archivo** .  Se admiten tres tipos de proyecto de sitio Web actualmente:  
  
-   Vacíe los proyectos de sitio Web  
  
-   Proyectos de sitio web  
  
-   Proyectos de servicio web  
  
### Proyectos vacíos del sitio Web  
 Estos archivos crean un nuevo sitio Web vacío en respuesta al comando de **sitio Web vacío** , que está disponible después de señalar a **Nuevo sitio web** en el menú de **Archivo** :  
  
-   EmptyWeb.vstemplate  
  
     El archivo de plantilla que dirige la creación del nuevo sitio Web vacío.  
  
-   EmptyWeb.webproj  
  
     Este archivo es un artefacto en la plantilla de proyecto.  Cumple la referencia de archivo de proyecto en el archivo de EmptyWeb.vstemplate.  
  
### Proyectos de sitio Web  
 Estos archivos se crea un nuevo sitio Web en respuesta al comando de **Sitio web ASP.NET** , que está disponible después de señalar a **Nuevo sitio web** en el menú de **Archivo** :  
  
-   Default.aspx  
  
     la página principal predeterminada para el nuevo sitio Web.  El atributo language especifica el lenguaje de codebehind, y el atributo CodeFile especifica el archivo dependiente que contiene el código de codebehind asociado a esta página.  
  
-   Default.aspx.*extensión*  
  
     El archivo dependiente que contiene el código de codebehind para la página principal predeterminada.  El lenguaje de codebehind determina *extensión* de este archivo.  
  
-   web.config  
  
     El archivo de configuración raíz web.site.  
  
-   WebApplication.vstemplate  
  
     El archivo de plantilla que determina el contenido de la solución en el sitio Web y fuerza la creación de la carpeta App\_Data.  
  
-   WebApplication.webproj  
  
     Este archivo es un artefacto en la plantilla de proyecto.  Cumple la referencia de archivo de proyecto en el archivo de WebApplication.vstemplate.  
  
### Proyectos de servicio web  
 Estos archivos se crea un nuevo sitio Web en respuesta al comando de **Servicio Web ASP.NET** disponible después de señalar a **Nuevo sitio web** en el menú de **Archivo** :  
  
-   Service.asmx  
  
     la página HTML para el nuevo servicio web.  El atributo language especifica el lenguaje de codebehind, y el atributo CodeBehind especifica el archivo dependiente que contiene el código de codebehind asociado a este servicio.  
  
-   servicio. *extensión*  
  
     el archivo dependiente que implementa la clase de servicio.  El lenguaje de codebehind determina *extensión* de este archivo.  
  
-   web.config  
  
-   El archivo de configuración raíz web.site.  
  
-   WebService.vstemplate  
  
     El archivo de plantilla que determina el contenido de la solución en el sitio Web y fuerza la creación de carpetas App\_Data y App\_Code.  el servicio. el archivo de*extensión* se copia en la carpeta App\_Code.  
  
-   WebService.webproj  
  
     Este archivo es un artefacto en la plantilla de proyecto.  Cumple la referencia de archivo de proyecto en el archivo de WebService.vstemplate.  
  
## Carpeta plantillas de elemento de proyecto  
 Las plantillas web de la plantilla de elemento de proyecto se instalan normalmente en \[*ruta de instalación de Visual Studio*\] \\Common7\\IDE\\ItemTemplates\\Web \\, cada uno en una subcarpeta denominada después del lenguaje de programación web.  
  
## Plantillas de elementos de proyecto  
 Las plantillas de elemento de proyecto de sitio Web se utilizan para agregar las nuevas páginas Web en un sitio Web en respuesta al comando de **Agregar elemento existente** .  estas clases de páginas Web se admiten actualmente:  
  
-   nueva clase  
  
-   nueva página HTML  
  
-   nuevo formulario web  
  
-   nueva página maestra  
  
### nueva clase  
 Esta plantilla crea un nuevo archivo de código fuente que define una clase vacía en respuesta al comando de **agregue la nueva clase** .  
  
-   clase. *extensión*  
  
     el archivo de código fuente que implementa la clase vacía.  El lenguaje de codebehind determina *extensión* de este archivo.  
  
-   Class.vstemplate  
  
     El archivo de plantilla que crea el archivo de código fuente y determina su contenido.  
  
### nueva página HTML  
 Esta plantilla crea una página Web en respuesta al comando de **agregue la nueva página HTML** .  
  
-   HTMLPage.htm  
  
     El contenido inicial de la página Web.  Esta página Web no suele ningún archivo asociado dependiente de codebehind.  Para crear una página automática con un archivo asociado de codebehind, use la plantilla de formulario web en su lugar.  
  
-   HTMLPage.vstemplate  
  
     El archivo de plantilla que crea la página Web y determina su contenido.  
  
### nuevo WebForm  
 Esta plantilla crea una página Web inteligente en respuesta al comando de **agregue el nuevo formulario web** .  
  
 Para crear un archivo de código fuente dependiente de codebehind, seleccione **Escriba código en archivo independiente**.  Si no una única página Web que se crea tiene un script vacío bloqueado y ninguna directiva de la página %\> de \<% enlazar un archivo dependiente.  
  
 Para crear una página de contenido de una página maestra seleccionada, seleccione **Página maestra seleccione**.  
  
-   WebForm.aspx  
  
     El contenido inicial de la página Web.  Esta página Web no tiene un archivo asociado dependiente de codebehind.  
  
-   WebForm\_cb.aspx  
  
     El contenido inicial de la página Web.  Esta página Web tiene asociado un archivo dependiente de codebehind.  
  
-   Codebehind. *extensión*  
  
     El archivo dependiente que implementa la clase de webform.  El lenguaje de codebehind determina *extensión* de este archivo.  
  
-   ContentPage.aspx  
  
     El contenido inicial de la página Web como una página de contenido.  Esta página Web no tiene un archivo asociado dependiente de codebehind.  
  
-   ContentPage\_cb.aspx  
  
     El contenido inicial de la página Web como una página de contenido.  Esta página Web tiene asociado un archivo dependiente de codebehind.  
  
-   WebForm.vstemplate  
  
     El archivo de plantilla que determina el contenido de la nueva página Web y su archivo dependiente, si existe.  
  
### nueva página maestra  
 Esta plantilla crea una nueva página maestra en respuesta al comando de **agregue la nueva página maestra** .  
  
 Para crear un archivo de código fuente dependiente de codebehind, seleccione **Escriba código en archivo independiente**.  Si no una única página Web que se crea tiene un script vacío bloqueado y ninguna directiva de la página %\> de \<% enlazar un archivo dependiente.  
  
-   MasterPage.master  
  
     El contenido inicial de la página maestra.  Esta página maestra no tiene ningún archivo asociado dependiente de codebehind.  
  
-   MasterPage\_cb.master  
  
     El contenido inicial de la página maestra.  Esta página maestra tiene asociado un archivo dependiente de codebehind.  
  
-   Codebehind.*extensión*  
  
     el archivo dependiente que implementa la clase de la página maestra.  El lenguaje de codebehind determina *extensión* de este archivo.  
  
-   MasterPage.vstemplate  
  
     El archivo de plantilla que determina el contenido de la nueva página maestra y su archivo dependiente, si existe.  
  
## Vea también  
 [Compatibilidad con sitios Web](../../extensibility/internals/web-site-support.md)