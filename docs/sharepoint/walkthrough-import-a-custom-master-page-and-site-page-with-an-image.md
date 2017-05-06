---
title: "Tutorial: Importar una p&#225;gina maestra personalizada y una p&#225;gina de sitio con una imagen"
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
helpviewer_keywords: 
  - "importar elementos [desarrollo de SharePoint en Visual Studio]"
  - "desarrollo de SharePoint en Visual Studio, importar elementos"
ms.assetid: d1703957-81e2-47e1-b4ca-6a8d550d8da2
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Tutorial: Importar una p&#225;gina maestra personalizada y una p&#225;gina de sitio con una imagen
  En este tutorial se demuestra cómo importar una página maestra personalizada de SharePoint y una página de sitio que contiene una imagen a un proyecto de SharePoint para [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 En este tutorial se muestra cómo llevar a cabo las tareas siguientes:  
  
-   Crear una página maestra personalizada y una página de sitio utilizando una imagen en SharePoint Designer.  
  
-   Exportar una página maestra personalizada, una imagen y una página de sitio a un archivo de solución de SharePoint \(.wsp\).  
  
-   Importar el archivo .wsp a un proyecto de SharePoint para [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e implementarlo mediante el proyecto Paquete de importación de la solución de SharePoint.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Requisitos previos  
 Para completar este tutorial, debe tener los componentes siguientes:  
  
-   Ediciones compatibles de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] y SharePoint.  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
-   SharePoint Designer 2010.  
  
## Crear elementos en SharePoint Designer  
 En este ejemplo se muestra cómo crear tres elementos en SharePoint Designer para la exportación: una página maestra personalizada, una página de sitio que hace referencia a la página maestra personalizada y un archivo de imagen que aparecerá en la página de sitio.  La imagen se agrega a la carpeta \/images\/ de SharePoint.  
  
#### Para crear una página maestra personalizada en SharePoint Designer  
  
1.  En SharePoint Designer, en el panel de navegación, elija el objeto de sitio de **Páginas maestras** .  
  
2.  En la cinta de opciones de **Páginas maestras** , elija **Página maestra en blanco**.  
  
3.  Elija la nueva página maestra y, a continuación, en la cinta de opciones de **Páginas maestras** , elija **Editar archivo**.  
  
4.  En la parte inferior de SharePoint Designer, elija la ficha de **code** .  
  
5.  Reemplace el marcado existente con el siguiente.  
  
    ```  
    <%@ Master Language="C#" %>  
    <%@ Register tagprefix="SharePoint" namespace="Microsoft.SharePoint.WebControls" assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <html dir="ltr">  
    <head runat="server">  
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">  
    <SharePoint:RobotsMetaTag runat="server" __designer:Preview="" __designer:Values="<P N='InDesign' T='False' /><P N='ID' T='ctl00' /><P N='Page' ID='1' /><P N='TemplateControl' ID='2' /><P N='AppRelativeTemplateSourceDirectory' R='-1' />"></SharePoint:RobotsMetaTag>  
    <title>Web Page</title>  
    </head>  
    <body>  
    <form id="form1" runat="server">  
    <asp:ContentPlaceHolder id="ContentPlaceHolderMain"   
            runat="server">  
          </asp:ContentPlaceHolder>  
    </form>  
    </body>  
    </html>  
    ```  
  
6.  Guarde la página, elija la ficha de **Páginas maestras** , y el nombre de la página maestra como **mybasic1.master**.  
  
## Agregar una imagen a la base de datos de contenido en SharePoint Designer  
 A continuación puede agregar una imagen para mostrar en la página de sitio.  La imagen se implementa en la base de datos de contenido de SharePoint.  
  
#### Para agregar una imagen a la base de datos de contenido en SharePoint Designer  
  
1.  En el panel de navegación, elija el objeto de sitio de **todos los archivos** y, a continuación, en la vista de árbol, seleccione la carpeta de **imágenes** .  
  
2.  En la cinta de opciones de **todos los archivos** , elija **Archivos de importación**, elija un archivo choice, y elija el botón de **Aceptar** .  En este ejemplo, el archivo se denomina **myimg1.png**.  
  
     Opcionalmente, puede crear una subcarpeta para ayudar a organizar las imágenes.  
  
3.  Cierre el cuadro de diálogo **Importar**.  
  
## Crear una página de sitio  
 Esta página de sitio básica usa la página maestra personalizada y muestra la imagen que agregó en el paso anterior.  
  
#### Para crear una página de sitio  
  
1.  En el panel de navegación, elija el objeto de **Páginas del sitio** .  
  
2.  En la cinta de opciones de **Páginas** , elija el botón de **Página** , elija el tipo de la página de **ASPX** , y llame al nuevo archivo **mycontentpage1.aspx**.  
  
     Opcionalmente, puede crear una subcarpeta para ayudar a organizar las páginas del sitio.  
  
3.  En la lista de páginas de sitio, elija **MyContentPage1.aspx** para abrir la página de propiedades y, a continuación, en la parte inferior de la página, elija el vínculo de **Editar archivo** .  
  
     Si aparece un mensaje y indica que esta página no contiene ningún regiones que son modificables en modo seguro y no pregunta si desea abrir esta página en modo avanzado, elija el botón de **Sí** .  
  
4.  En la parte inferior de la página, elija el botón de **code** .  
  
5.  Reemplace el marcado existente con el siguiente.  
  
    ```  
    <%@ Import Namespace="Microsoft.SharePoint.ApplicationPages" %>  
    <%@ Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Register Tagprefix="Utilities" Namespace="Microsoft.SharePoint.Utilities" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Register Tagprefix="asp" Namespace="System.Web.UI" Assembly="System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" %>  
    <%@ Import Namespace="Microsoft.SharePoint" %>  
    <%@ Assembly Name="Microsoft.Web.CommandUI, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Page Language="C#" Inherits="Microsoft.SharePoint.WebControls.LayoutsPageBase" MasterPageFile="../_catalogs/masterpage/mybasic1.master" meta:progid="SharePoint.WebPartPage.Document" %>  
  
    <asp:Content ID="Main" ContentPlaceHolderID="ContentPlaceHolderMain" runat="server">  
    <img alt="My Image" longdesc="My image from images folder" src="../images/myimg1.png" />  
    </asp:Content>  
    ```  
  
6.  Guarde la página de sitio actualizada.  
  
## Exportar los elementos de SharePoint  
 Exporte los elementos de SharePoint a un archivo de solución de SharePoint \(.wsp\).  
  
#### Para exportar los elementos de SharePoint Designer  
  
1.  En SharePoint Designer, en el panel de navegación, elija el objeto de **Sitio de grupo** y, a continuación, en la cinta de opciones de **sitio** , elija **Guardar como plantilla**.  
  
2.  En el cuadro de diálogo de **Guardar como plantilla** , escriba un nombre de archivo y de la plantilla, active la casilla de **Incluya el contenido** , y después elija el botón de **Aceptar** .  
  
     Esto guarda el contenido del sitio en el archivo .wsp.  
  
3.  Una vez exportada la solución, elija el vínculo de **Galería de soluciones** para mostrar la lista de archivos de solución disponibles.  
  
4.  Abrir el menú contextual para el nuevo archivo .wsp y, a continuación **Guardar destino como** guardarlo en el sistema.  
  
## Importar los elementos a Visual Studio  
 Importe el archivo .wsp en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Una vez importado el contenido, puede personalizarlo, agregar más elementos, y después se implementan.  
  
#### Para importar elementos del archivo .wsp a Visual Studio  
  
1.  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], cree un proyecto de**Paquete de solución de SharePoint 2010 de importación** .  
  
2.  En la página de **Seleccione los elementos que desea importar** , en **Módulo** en la columna de **Tipo** , active las casillas de sólo los archivos en la tabla siguiente para importarlos.  
  
    |Nombre de archivo|Descripción|  
    |-----------------------|-----------------|  
    |\_catalogsmasterpage\_|Página maestra personalizada.|  
    |images\_|Archivo de imagen del sistema de archivos de SharePoint.|  
    |SitePages\_|Página de sitio.|  
  
3.  Elija el botón de **Finalizar** para importar los elementos seleccionados.  
  
4.  En **Explorador de soluciones**, elija el nodo de \_catalogsmasterpage\_, y establezca el valor de la propiedad de **Resolución de conflictos de implementación** a **Automático**.  
  
     Esto ayuda a asegurarse de que los conflictos de implementación se resuelvan automáticamente.  
  
5.  Si la nueva página maestra tiene el mismo nombre que una página existente, asegúrese de que la página existente no está marcada como página maestra predeterminada o página maestra personalizada en SharePoint Designer.  
  
     Si una página maestra existente está marcada como página maestra predeterminada o página maestra personalizada, recibirá un error de implementación que indica que no se puede eliminar la página maestra.  Para evitar este problema, haga lo siguiente:  
  
    -   Si la página maestra existente está establecida como página maestra predeterminada, establezca temporalmente otra página maestra como página maestra predeterminada.  Después de implementar los archivos en SharePoint, establezca la nueva página maestra como página maestra predeterminada.  
  
    -   Si la página maestra existente está establecida como página maestra personalizada, establezca temporalmente otra página maestra como página maestra personalizada.  Después de implementar los archivos en SharePoint, establezca la nueva página maestra como página maestra personalizada.  
  
6.  En la barra de menú, elija **Compilación**, **Implementar solución**.  
  
7.  Abra el sitio de SharePoint para ver los elementos implementados.  
  
 Una manera alternativa de importar los archivos a [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e implementarlos en SharePoint consiste en agregar los archivos a los módulos de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Cómo: Importar un tema o página maestra](../sharepoint/how-to-import-a-master-page-or-theme.md) y [Utilizar módulos para incluir archivos en la solución](../sharepoint/using-modules-to-include-files-in-the-solution.md).  
  
## Vea también  
 [Importar elementos de un sitio de SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Crear controles reutilizables para elementos web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  