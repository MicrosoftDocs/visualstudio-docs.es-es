---
title: 'Tutorial: Crear una página de aplicación de SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 52ff6b3431ac3f87c85eefcf728cfe4c4875f884
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42634792"
---
# <a name="walkthrough-create-a-sharepoint-application-page"></a>Tutorial: Crear una página de aplicación de SharePoint
 
Una página de aplicación es una forma especializada de una página ASP.NET. Las páginas de aplicación incluyen contenido que se combina con una página principal de SharePoint. Para obtener más información, consulte [crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

En este tutorial se muestra cómo crear una página de aplicación y depurarla utilizando un sitio de SharePoint local. Esta página muestra todos los elementos que cada usuario ha creado o modificado en todos los sitios de la granja de servidores.

En este tutorial se muestran las tareas siguientes:

- Crear un proyecto de SharePoint.
- Agregar una página de aplicación al proyecto de SharePoint.
- Agregar controles ASP.NET a la página de aplicación.
- Agregar código detrás de los controles ASP.NET.
- Probar la página de aplicación.

> [!NOTE]
> Es posible que el equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos

- Ediciones compatibles de Windows y SharePoint.

## <a name="create-a-sharepoint-project"></a>Crear un proyecto de SharePoint

En primer lugar, cree un **proyecto vacío de SharePoint**. Más adelante, agregará un **página aplicación** a este proyecto.

1. Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Abra el **nuevo proyecto** cuadro de diálogo, expanda el **Office/SharePoint** nodo bajo el lenguaje que desee usar y, a continuación, elija el **soluciones de SharePoint** nodo.

3. En el **plantillas instaladas de Visual Studio** panel, elija el **SharePoint 2010 - proyecto vacío** plantilla. Denomine el proyecto **MySharePointProject**y, a continuación, elija el **Aceptar** botón.

     El **Asistente de personalización de SharePoint** aparece. Este asistente permite seleccionar el sitio que se va a usar para depurar el proyecto, así como el nivel de confianza de la solución.

4. Elija la **implementar como solución de granja de servidores** botón de opción y, a continuación, elija el **finalizar** botón para aceptar el sitio local predeterminado de SharePoint.

## <a name="create-an-application-page"></a>Crear una página de aplicación

Para crear una página de aplicación, agregue un **página aplicación** al proyecto.

1. En **el Explorador de soluciones**, elija el **MySharePointProject** proyecto.

2. En la barra de menús, elija **Proyecto** >  **Agregar nuevo elemento**.

3. En el **Agregar nuevo elemento** diálogo cuadro, elija el **página de la aplicación (solución de granja de servidores únicamente** plantilla.

4. Nombre de la página **SearchItems**y, a continuación, elija el **agregar** botón.

     El Diseñador de Visual Web Developer muestra la página de aplicación en **origen** donde puede ver los elementos HTML de la página de vista. El diseñador muestra el marcado para varios <xref:System.Web.UI.WebControls.Content> controles. Cada control se asigna a un <xref:System.Web.UI.WebControls.ContentPlaceHolder> control que se define en la página principal de aplicación predeterminado.

## <a name="design-the-layout-of-the-application-page"></a>Definir el diseño de la página de aplicación

El elemento de la página de aplicación le permite usar un diseñador para agregar controles ASP.NET a la página de aplicación. Este diseñador es el mismo diseñador que se usan en Visual Web Developer. Agregar una etiqueta, una lista de botones de radio y una tabla a la **origen** ver del diseñador y, a continuación, establezca las propiedades tal como lo haría cuando diseña cualquier página ASP.NET estándar.

1. En la barra de menús, elija **vista** > **cuadro de herramientas**.

2. En el nodo estándar de la **cuadro de herramientas**, realice uno de los pasos siguientes:

    - Abra el menú contextual para el **etiqueta** de elemento, elija **copia**, abra el menú contextual de la línea bajo el **PlaceHolderMain** control en el diseñador, de contenido y, a continuación, Elija **pegar**.

    - Arrastre el **etiqueta** elemento desde el **cuadro de herramientas** hasta el cuerpo de la **PlaceHolderMain** control de contenido.

3. Repita el paso anterior para agregar un **DropDownList** elemento y un **tabla** elemento a la **PlaceHolderMain** control de contenido.

4. En el diseñador, cambie el valor de la `Text` atributo del control de etiqueta para **mostrar todos los elementos**.

5. En el diseñador, reemplace el `<asp:DropDownList>` elemento con el siguiente código XML.

    ```xml
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>
    </asp:DropDownList>
    ```

## <a name="handle-the-events-of-controls-on-the-page"></a>Controlar los eventos de controles de la página

Controle los controles en una página de aplicación tal como lo haría con cualquier página ASP.NET. En este procedimiento, va a controlar el `SelectedIndexChanged` eventos de la lista desplegable.

1. En el **vista** menú, elija **código**.

     El archivo de código de la página de aplicación se abre en el Editor de código.

2. Agregue el método siguiente a la clase `SearchItems`. Este código controla el <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged> eventos de la <xref:System.Web.UI.WebControls.DropDownList> mediante una llamada a un método que creará más adelante en este tutorial.

     [!code-vb[SP_ApplicationPage#5](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]
     [!code-csharp[SP_ApplicationPage#5](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]

3. Agregue las siguientes instrucciones al principio del archivo de código de la página de aplicación.

     [!code-vb[SP_ApplicationPage#1](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]
     [!code-csharp[SP_ApplicationPage#1](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]

4. Agregue el método siguiente a la clase `SearchItems`. Este método recorre en iteración todos los sitios de la granja de servidores y busca los elementos creados o modificados por el usuario actual.

     [!code-vb[SP_ApplicationPage#2](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]
     [!code-csharp[SP_ApplicationPage#2](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]

5. Agregue el método siguiente a la clase `SearchItems`. Este método muestra elementos creados o modificados por el usuario actual en la tabla.

     [!code-vb[SP_ApplicationPage#3](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]
     [!code-csharp[SP_ApplicationPage#3](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]

## <a name="test-the-application-page"></a>Probar la página de aplicación

Al ejecutar el proyecto, se abre el sitio de SharePoint y aparece la página de aplicación.

1. En **el Explorador de soluciones**, abra el menú contextual de la página de aplicación y, a continuación, elija **establecer como elemento de inicio**.

2. Elija la tecla **F5**.

     Se abre el sitio de SharePoint.

3. En la página de aplicación, elija el **modificado por mí** opción.

     La página de aplicación se actualiza y muestra todos los elementos que ha modificado en todos los sitios de la granja de servidores.

4. En la página de aplicación, elija **creados por mí** en la lista.

     La página de aplicación se actualiza y muestra todos los elementos que ha creado en todos los sitios de la granja de servidores.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información acerca de las páginas de aplicación de SharePoint, vea [crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

Puede aprender más sobre cómo diseñar el contenido de la página de SharePoint mediante el Diseñador Web Visual en los siguientes temas:

- [Crear elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

- [Crear controles reutilizables para elementos web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>Vea también

[Cómo: crear una página de aplicación](../sharepoint/how-to-create-an-application-page.md)  
[Tipo de página _layouts de aplicaciones](http://go.microsoft.com/fwlink/?LinkID=169274)
