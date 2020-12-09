---
title: 'Tutorial: crear una página de aplicación de SharePoint | Microsoft Docs'
description: En este tutorial, cree una página de aplicación (una forma especializada de una página de ASP.NET) y, a continuación, depure mediante un sitio de SharePoint local.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 95addb145312de85a3525c228297e7ff9636ea0d
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914886"
---
# <a name="walkthrough-create-a-sharepoint-application-page"></a>Tutorial: Creación de una página de aplicación de SharePoint

Una página de aplicación es una forma especializada de una página ASP.NET. Las páginas de aplicación contienen contenido que se combina con una página maestra de SharePoint. Para obtener más información, vea [crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

En este tutorial se muestra cómo crear una página de aplicación y, a continuación, depurarla mediante un sitio de SharePoint local. Esta página muestra todos los elementos que cada usuario ha creado o modificado en todos los sitios de la granja de servidores.

En este tutorial se muestran las tareas siguientes:

- Crear un proyecto de SharePoint.
- Agregar una página de aplicación al proyecto de SharePoint.
- Agregar controles ASP.NET a la página de la aplicación.
- Agregar código detrás de los controles ASP.NET.
- Prueba de la página de la aplicación.

> [!NOTE]
> Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos

- Ediciones compatibles de Windows y SharePoint.

## <a name="create-a-sharepoint-project"></a>Crear un proyecto de SharePoint

En primer lugar, cree un **proyecto de SharePoint vacío**. Más adelante, agregará un elemento de **Página de aplicación** a este proyecto.

1. Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Abra el cuadro de diálogo **nuevo proyecto** , expanda el nodo **Office/SharePoint** bajo el lenguaje que desea usar y, a continuación, elija el nodo **soluciones de SharePoint** .

3. En el panel **plantillas instaladas de Visual Studio** , elija la plantilla **de proyecto SharePoint 2010-Empty** . Asigne al proyecto el nombre **MySharePointProject** y, a continuación, elija el botón **Aceptar** .

     Aparece el **Asistente para la personalización de SharePoint** . Este asistente permite seleccionar el sitio que se va a usar para depurar el proyecto, así como el nivel de confianza de la solución.

4. Elija el botón de opción **implementar como solución de granja de servidores** y, después, elija el botón **Finalizar** para aceptar el sitio local predeterminado de SharePoint.

## <a name="create-an-application-page"></a>Crear una página de aplicación

Para crear una página de aplicación, agregue un elemento de **Página de aplicación** al proyecto.

1. En **Explorador de soluciones**, elija el proyecto **MySharePointProject** .

2. En la barra de menús, elija **Proyecto** >  **Agregar nuevo elemento**.

3. En el cuadro de diálogo **Agregar nuevo elemento** , elija la plantilla **Página de aplicación (solo solución de granja de servidores** ).

4. Asigne a la página el nombre **SearchItems** y, a continuación, elija el botón **Agregar** .

     El diseñador de Visual Web Developer muestra la página de aplicación en la vista **código fuente** , donde puede ver los elementos HTML de la página. El diseñador muestra el marcado de varios <xref:System.Web.UI.WebControls.Content> controles. Cada control se asigna a un <xref:System.Web.UI.WebControls.ContentPlaceHolder> control que se define en la página maestra de aplicación predeterminada.

## <a name="design-the-layout-of-the-application-page"></a>Diseñar el diseño de la página de la aplicación

El elemento de página de aplicación le permite usar un diseñador para agregar controles ASP.NET a la página de la aplicación. Este diseñador es el mismo diseñador que se utiliza en Visual Web Developer. Agregue una etiqueta, una lista de botones de radio y una tabla a la vista de **código fuente** del diseñador y, a continuación, establezca las propiedades del mismo modo que lo haría al diseñar cualquier página de ASP.net estándar.

1. En la barra de menús, elija **Ver**  >  **cuadro de herramientas**.

2. En el nodo estándar del **cuadro de herramientas**, realice uno de los pasos siguientes:

    - Abra el menú contextual del elemento de **etiqueta** , elija **copiar**, abra el menú contextual de la línea en el control de contenido **PlaceHolderMain** en el diseñador y, a continuación, elija **pegar**.

    - Arrastre el elemento **etiqueta** desde el **cuadro de herramientas** hasta el cuerpo del control de contenido **PlaceHolderMain** .

3. Repita el paso anterior para agregar un elemento **DropDownList** y un elemento de **tabla** al control de contenido **PlaceHolderMain** .

4. En el diseñador, cambie el valor del `Text` atributo del control etiqueta para **Mostrar todos los elementos**.

5. En el diseñador, reemplace el `<asp:DropDownList>` elemento por el siguiente código XML.

    ```xml
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>
    </asp:DropDownList>
    ```

## <a name="handle-the-events-of-controls-on-the-page"></a>Controlar los eventos de los controles de la página

Controle los controles en una página de aplicación de la misma forma que lo haría con cualquier página de ASP.NET. En este procedimiento, se controlará el `SelectedIndexChanged` evento de la lista desplegable.

1. En el menú **Ver** , elija **código**.

     El archivo de código de la página de la aplicación se abre en el editor de código.

2. Agrega el método siguiente a la clase `SearchItems`: Este código controla el <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged> evento de <xref:System.Web.UI.WebControls.DropDownList> llamando a un método que se creará más adelante en este tutorial.

     [!code-vb[SP_ApplicationPage#5](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]
     [!code-csharp[SP_ApplicationPage#5](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]

3. Agregue las siguientes instrucciones a la parte superior del archivo de código de la página de la aplicación.

     [!code-vb[SP_ApplicationPage#1](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]
     [!code-csharp[SP_ApplicationPage#1](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]

4. Agrega el método siguiente a la clase `SearchItems`: Este método recorre en iteración todos los sitios de la granja de servidores y busca los elementos creados o modificados por el usuario actual.

     [!code-vb[SP_ApplicationPage#2](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]
     [!code-csharp[SP_ApplicationPage#2](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]

5. Agrega el método siguiente a la clase `SearchItems`: Este método muestra los elementos creados o modificados por el usuario actual en la tabla.

     [!code-vb[SP_ApplicationPage#3](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]
     [!code-csharp[SP_ApplicationPage#3](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]

## <a name="test-the-application-page"></a>Probar la página de aplicación

Al ejecutar el proyecto, se abre el sitio de SharePoint y aparece la página de aplicación.

1. En **Explorador de soluciones**, abra el menú contextual de la página de la aplicación y, a continuación, elija **establecer como elemento de inicio**.

2. Elija la tecla **F5**.

     Se abre el sitio de SharePoint.

3. En la página de la aplicación, elija la opción **modificado por mí** .

     La página de aplicación se actualiza y muestra todos los elementos que ha modificado en todos los sitios de la granja de servidores.

4. En la página aplicación, elija **creado por mí** en la lista.

     La página de aplicación se actualiza y muestra todos los elementos que ha creado en todos los sitios de la granja de servidores.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información acerca de las páginas de aplicación de SharePoint, vea [crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

Puede obtener más información sobre cómo diseñar el contenido de una página de SharePoint mediante el diseñador web visual de estos temas:

- [Crear elementos Web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

- [Crear controles reutilizables para elementos Web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>Consulte también

[Cómo: crear una página](../sharepoint/how-to-create-an-application-page.md) 
 de aplicación [Tipo de página _layouts de aplicación](/previous-versions/office/aa979604(v=office.14))
