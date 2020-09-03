---
title: Importar página maestra personalizada & página de sitio con imagen
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 311124b2e0b81e70c4c2a7b40754207e6c66b749
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015687"
---
# <a name="walkthrough-import-a-custom-master-page-and-site-page-with-an-image"></a>Tutorial: importar una página maestra personalizada y una página de sitio con una imagen
  En este tutorial se muestra cómo importar una página maestra personalizada de SharePoint y una página de sitio que tiene una imagen en un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proyecto de SharePoint.

 En este tutorial se muestra cómo llevar a cabo las tareas siguientes:

- Crear una página maestra personalizada y una página de sitio mediante una imagen en SharePoint Designer.

- Exportar una página maestra personalizada, una imagen y una página de sitio a un archivo de solución de SharePoint (*. wsp*).

- Importe e implemente el archivo *. wsp* en un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proyecto de SharePoint mediante el proyecto importar paquete de solución de SharePoint.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos
 Para completar este tutorial, debe disponer de los siguientes componentes:

- Ediciones compatibles de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] y SharePoint.

- Visual Studio.

- SharePoint Designer 2010.

## <a name="create-items-in-sharepoint-designer"></a>Crear elementos en SharePoint Designer
 En este ejemplo se muestra cómo crear tres elementos en SharePoint Designer para la exportación: una página maestra personalizada, una página del sitio que hace referencia a la página maestra personalizada y un archivo de imagen para que aparezca en la página del sitio. La imagen se agrega a la carpeta/images/en SharePoint.

#### <a name="to-create-a-custom-master-page-in-sharepoint-designer"></a>Para crear una página maestra personalizada en SharePoint Designer

1. En SharePoint Designer, en el panel de navegación, elija el objeto de sitio **páginas maestras** .

2. En la cinta **páginas maestras** , elija **página maestra en blanco**.

3. Elija la nueva página maestra y, a continuación, en la cinta **páginas maestras** , elija **Editar archivo**.

4. En la parte inferior de SharePoint Designer, elija la pestaña **código** .

5. Reemplace el marcado existente por el marcado siguiente.

    ```aspx-csharp
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

6. Guarde la página, elija la pestaña **páginas maestras** y cambie el nombre de la página maestra a **mybasic1. Master**.

## <a name="add-an-image-to-the-content-database-in-sharepoint-designer"></a>Agregar una imagen a la base de datos de contenido en SharePoint Designer
 Ahora puede Agregar una imagen para que se muestre en la página del sitio. La imagen se implementa en la base de datos de contenido de SharePoint.

#### <a name="to-add-an-image-to-the-content-database-in-sharepoint-designer"></a>Para agregar una imagen a la base de datos de contenido en SharePoint Designer

1. En el panel de navegación, elija el objeto de sitio **todos los archivos** y, a continuación, en la vista de árbol, elija la carpeta **imágenes** .

2. En la cinta **todos los archivos** , elija **importar archivos**, elija el archivo que desee y, a continuación, elija el botón **Aceptar** . En este ejemplo, el archivo se denomina **myimg1.png**.

     Opcionalmente, puede crear una subcarpeta para ayudar a organizar las imágenes.

3. Cierre el cuadro de diálogo **importar** .

## <a name="create-a-site-page"></a>Página crear un sitio
 En esta página de sitio básico se usa la página maestra personalizada y se muestra la imagen que agregó en el paso anterior.

#### <a name="to-create-a-site-page"></a>Para crear una página de sitio

1. En el panel de navegación, elija el objeto **páginas del sitio** .

2. En la cinta de opciones de **páginas** , elija el botón de **Página** , elija el tipo de página **aspx** y, a continuación, asigne al nuevo archivo el nombre **mycontentpage1. aspx**.

     Opcionalmente, puede crear una subcarpeta que le ayude a organizar las páginas del sitio.

3. En la lista páginas del sitio, elija **MyContentPage1. aspx** para abrir su página de propiedades y, a continuación, en la parte inferior de la página, elija el vínculo **Editar archivo** .

     Si aparece un mensaje que indica que esta página no contiene ninguna región que se pueda editar en modo seguro y pregunta si desea abrir esta página en modo avanzado, elija el botón **sí** .

4. En la parte inferior de la página, elija el botón **código** .

5. Reemplace el marcado existente por el marcado siguiente.

    ```aspx-csharp
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

6. Guarde la página del sitio actualizado.

## <a name="export-the-items-from-sharepoint"></a>Exportar los elementos de SharePoint
 Exporte los elementos de SharePoint a un archivo de solución de SharePoint (*. wsp*).

#### <a name="to-export-items-from-sharepoint-designer"></a>Para exportar elementos de SharePoint Designer

1. En SharePoint Designer, en el panel de navegación, elija el objeto de **sitio de grupo** y, a continuación, en la cinta **sitio** , elija **Guardar como plantilla**.

2. En el cuadro de diálogo **Guardar como plantilla** , escriba un nombre de archivo y un nombre de plantilla, active la casilla **incluir contenido** y, a continuación, elija el botón **Aceptar** .

     Esto guarda el contenido del sitio en el archivo *. wsp* .

3. Una vez que se haya exportado la solución, elija el vínculo **Galería de soluciones** para mostrar la lista de archivos de solución disponibles.

4. Abra el menú contextual del nuevo archivo *. wsp* y, a continuación, elija **Guardar destino como** para guardarlo en el sistema.

## <a name="import-the-items-into-visual-studio"></a>Importar los elementos en Visual Studio
 Importe el archivo *. wsp* en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Una vez importado el contenido, puede personalizarlo, agregar más elementos y, a continuación, implementarlo.

#### <a name="to-import-items-from-the-wsp-file-into-visual-studio"></a>Para importar elementos del archivo. wsp en Visual Studio

1. En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , cree un proyecto de **paquete de solución de SharePoint 2010 de importación** .

2. En la página **seleccionar los elementos que se van a importar** , en **módulo** en la columna **tipo** , active las casillas de los archivos de la tabla siguiente para la importación.

   | Nombre de archivo | Descripción |
   |------------------------|-----------------------------------------------|
   | \_catalogsmasterpage\_ | La página maestra personalizada. |
   | images_ | El archivo de imagen en el sistema de archivos de SharePoint. |
   | SitePages_ | Página del sitio. |

3. Elija el botón **Finalizar** para importar los elementos seleccionados.

4. En **Explorador de soluciones**, elija el \_ \_ nodo catalogsmasterpage y establezca el valor de su propiedad **resolución de conflictos de implementación** en **automático**.

    Esto ayuda a garantizar que los conflictos de implementación se resuelvan automáticamente.

5. Si la nueva página maestra tiene el mismo nombre que una página existente, asegúrese de que la página existente no esté marcada como página maestra predeterminada o como página maestra personalizada en SharePoint Designer.

    Si una página maestra existente se marca como página maestra predeterminada o como página maestra personalizada, obtendrá un error de implementación que indica que no se puede eliminar la página maestra. Para evitar este problema, haga lo siguiente:

   - Si la página maestra existente está establecida como página maestra predeterminada, establezca temporalmente otra página maestra como página maestra predeterminada. Después de implementar los archivos en SharePoint, establezca la nueva página maestra como página maestra predeterminada.

   - Si la página maestra existente está establecida como página maestra personalizada, establezca temporalmente otra página maestra como página maestra personalizada. Después de implementar los archivos en SharePoint, establezca la nueva página maestra como página maestra personalizada.

6. En la barra de menús, elija **compilar**  >  **implementar solución**.

7. Abra el sitio de SharePoint para ver los elementos implementados.

   Una manera alternativa de importar archivos [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e implementarlos en SharePoint es agregar los archivos a los módulos de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Cómo: importar una página maestra o un tema](../sharepoint/how-to-import-a-master-page-or-theme.md) y [usar módulos para incluir archivos en la solución](../sharepoint/using-modules-to-include-files-in-the-solution.md).

## <a name="see-also"></a>Consulte también
- [Importar elementos de un sitio de SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Crear controles reutilizables para elementos Web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
