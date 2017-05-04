---
title: "Tutorial: Importar elementos de un sitio de SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "importar elementos [desarrollo de SharePoint en Visual Studio]"
  - "desarrollo de SharePoint en Visual Studio, importar elementos"
ms.assetid: faac3309-88d7-4fb2-8392-feda07fc00e5
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Tutorial: Importar elementos de un sitio de SharePoint
  En este tutorial se muestra cómo importar elementos de un sitio de SharePoint existente en un proyecto de SharePoint de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 En este tutorial se muestran las siguientes tareas:  
  
-   Personalizar un sitio de SharePoint agregando una columna de sitio personalizada \(también conocida como *campo*.  
  
-   Exportar un sitio de SharePoint a un archivo .wsp.  
  
-   Importar el archivo .wsp en SharePoint de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utilizando el proyecto de importación .wsp.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] y SharePoint.  Para obtener más información, vea [Requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## Personalizar un sitio de SharePoint  
 Para este ejemplo, creará y personalizará un subsitio de SharePoint agregándole una nueva columna y creando otro subsitio para un uso posterior.  Después, exportará el primero subsitio a un archivo .wsp y, a continuación, importará la columna de sitio personalizada en el segundo subsitio utilizando el proyecto de importación .wsp.  
  
#### Para crear y personalizar un sitio de SharePoint  
  
1.  Abra un sitio de SharePoint mediante un explorador web, como http:\/\/*system name*\/SitePages\/Home.aspx.  
  
2.  Cree un subsitio fuera del sitio de SharePoint principal abriendo el menú de **Acciones del sitio** y elige **Nuevo sitio**.  
  
3.  En el cuadro de diálogo de **crear** de sitio, elija el tipo de **Esconda el sitio** .  
  
4.  En el cuadro de **title** , escriba columna sitio prueba 1; en el cuadro de **Nombre de la dirección URL** , escriba columnaprueba1; deje los otros valores en sus valores predeterminados; y después elija el botón de **crear** .  
  
5.  Una vez creado el sitio, retroceda en el explorador de nuevo el sitio principal, http:\/\/*system name*\/SitePages\/Home.aspx.  
  
6.  Una vez más crear un subsitio en blanco fuera del sitio de SharePoint principal abriendo el menú de **Acciones del sitio** , eligiendo **Nuevo sitio**, y después elegir el tipo de **Sitio en blanco** .  
  
7.  En el cuadro de **title** , escriba columna sitio prueba 2; en el cuadro de **Nombre de la dirección URL** , escriba columnaprueba2; deje los otros valores en sus valores predeterminados; y después elija el botón de **crear** .  
  
8.  Retroceda hasta el primero subsitio, http:\/\/*SystemName*\/columntest1\/default.aspx.  
  
9. En el menú de **Acciones del sitio** , elija **Configuración del sitio** para mostrar la página Configuración del sitio.  
  
10. En la sección de **Galerías** , elija el vínculo de **Columnas de sitio** .  
  
11. En la parte superior de la página de **Galería de columnas de sitio** , elija el botón de **crear** .  
  
12. En el cuadro de **Nombre de columna** , escriba columna prueba, mantenga los demás valores predeterminados, y elija el botón de **Aceptar** .  
  
13. La columna de **Pruebe la columna** aparece bajo el encabezado columnas personalizadas de la galería de columnas de sitio.  
  
## Exportar el sitio de SharePoint  
 A continuación, obtenga un archivo de instalación de SharePoint \(.wsp\) que contenga los elementos de SharePoint y los elementos que desea importar en el proyecto de SharePoint de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Si aún no tiene un archivo .wsp, debe crear uno a partir de un sitio de SharePoint existente.  Para este ejemplo, exportará el sitio de SharePoint predeterminado a un archivo .wsp.  
  
> [!IMPORTANT]  
>  Si recibe un error en tiempo de ejecución cuando lleva a cabo el procedimiento siguiente, tiene que realizar el procedimiento en un sistema con acceso al sitio de SharePoint.  
  
#### Para exportar un sitio de SharePoint existente  
  
1.  En el sitio de SharePoint, elija **Configuración del sitio** en la pestaña de **Acciones del sitio** para mostrar la página configuración del sitio.  
  
2.  En la sección de **Acciones del sitio** de la página Configuración del sitio, elija el vínculo de **Guarde el sitio como plantilla** .  
  
3.  En el cuadro **Nombre de archivo**, escriba SitioEjemplo y en el cuadro **Nombre de plantilla**, escriba Sitio de ejemplo.  
  
4.  Para este ejemplo, no active la casilla **Incluir contenido**.  
  
     Si activa esta casilla, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] guardará todas las listas y bibliotecas de documentos así como su contenido en el archivo .wsp.  Aunque esto es útil en algunas circunstancias, no se requiere con este ejemplo.  
  
5.  Cuando la operación se completa correctamente, elija el vínculo de **galería de soluciones** para ver el archivo .wsp.  
  
     Para ver la página de la galería de soluciones más adelante, abra el menú de **Acciones del sitio** , elija **Configuración del sitio**, elija el vínculo de **Vaya a la configuración del sitio de nivel superior** en la sección de **Administración de colección de sitios** , y elija el vínculo de **Soluciones** en la sección de **Galerías** .  
  
6.  En la galería de soluciones, elija el vínculo de **ExampleSite** .  
  
7.  En el cuadro de diálogo de **Descarga de archivos** , elija el botón de **Guardar** para guardar el archivo en el sistema local, de forma predeterminada, en la carpeta de descargas.  
  
## Importar el archivo .wsp  
 Ahora que tiene un archivo .wsp que contiene un elemento que desea reutilizar \(la columna de sitio personalizada Columna prueba\), importe el archivo .wsp para tener acceso a él.  
  
#### Para importar un archivo .wsp  
  
1.  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], en la barra de menú, elija **archivo**, **new**, **Project** para mostrar el cuadro de diálogo de **Nuevo proyecto** .  Si el IDE está establecido para utilizar la configuración de desarrollo de Visual Basic, en la barra de menú, elija **archivo**, **Nuevo proyecto**.  
  
2.  Expanda el nodo de **sharepoint** en **Visual C\#** o **Visual Basic**y, a continuación el nodo de **2010** .  
  
3.  Elija la plantilla de **Importar paquetes de soluciones de SharePoint 2010** en el panel de **Plantillas** , deje el nombre del proyecto como WspImportProject1, y elija el botón de **Aceptar** .  
  
     Aparece el **Asistente para personalización de SharePoint**.  
  
4.  En la página de **Especifique el sitio y el nivel de seguridad de la depuración** , entre en [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] para el segundo subsitio de SharePoint que creó anteriormente.  Agregará el nuevo elemento de campo personalizado, http:\/\/*system name*\/columntest2, a ese subsitio.  
  
5.  En la sección **¿Cuál es el nivel de confianza de esta solución de SharePoint?**, deje la selección como **Implementar como solución en espacio aislado**.  
  
6.  En la página de **Especifique el nuevo origen del proyecto** , vaya a la ubicación del sistema donde se previamente y después guardó el archivo .wsp elija el botón de **siguiente** .  
  
    > [!NOTE]  
    >  Si elige el botón de **Finalizar** en esta página, todos los elementos disponibles en el archivo .wsp se importarán.  
  
7.  En el cuadro de **Seleccione los elementos que desea importar** , desactive todas las casillas de la lista salvo de **Columna prueba**, y elija el botón de **Finalizar** .  
  
     Dado que la lista contiene muchos elementos, puede elegir las teclas Ctrl \+ de A para elegir todos los elementos en la lista, elija la BARRA ESPACIADORA para desactivar todas las casillas, y seleccione sólo la casilla situada junto al elemento de **Pruebe la columna** .  
  
     Una vez finalizada la operación de importación, un nuevo proyecto denominado **WspImportProject1** se crea con una carpeta denominada **Campos**.  En esta carpeta está la columna del sitio personalizada **Columna prueba** y su archivo de definición Elements.xml.  
  
## Implementar el proyecto  
 Finalmente, implemente **WspImportProject1** en el segundo subsitio de SharePoint que creó anteriormente para ver la columna de sitio personalizada.  
  
#### Para implementar el proyecto  
  
1.  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], elija la tecla F5 para implementar y ejecutar el proyecto de importación .wsp.  
  
2.  En el sitio de SharePoint, abra el menú de **Acciones del sitio** y, a continuación **Configuración del sitio** para mostrar la página Configuración del sitio.  
  
3.  En la sección de **Galerías** , elija el vínculo de **Columnas de sitio** .  
  
4.  Desplácese hasta la sección **Columnas personalizadas**.  
  
     Observe que la columna de sitio personalizada que importó del primer sitio de SharePoint aparece en la lista.  
  
## Vea también  
 [Importar elementos de un sitio de SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Crear controles reutilizables para elementos web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  