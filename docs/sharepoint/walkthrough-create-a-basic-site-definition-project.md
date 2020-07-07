---
title: 'Tutorial: crear un proyecto de definición de sitio básico | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d1c06f4df5d1efe06ad2537bd2e65f2c239f3be2
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016771"
---
# <a name="walkthrough-create-a-basic-site-definition-project"></a>Tutorial: crear un proyecto de definición de sitio básico
  En este tutorial se muestra cómo crear una definición de sitio básica que contiene un elemento Web visual con algunos controles. Por motivos de claridad, el elemento Web visual que cree tiene solo unos pocos controles. Sin embargo, puede crear definiciones de sitios de SharePoint más sofisticadas que incluyan más funcionalidad.

 En este tutorial se muestran las siguientes tareas:

- Crear una definición de sitio mediante la [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] plantilla de proyecto.

- Crear un sitio de SharePoint mediante una definición de sitio en SharePoint.

- Agregar un elemento Web visual a la solución.

- Personalizar la página default. aspx del sitio agregando el nuevo elemento Web visual.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- Ediciones compatibles de Microsoft Windows y SharePoint. Para obtener más información, vea requisitos para desarrollar soluciones de SharePoint.

- Visual Studio.

## <a name="create-a-site-definition-solution"></a>Crear una solución de definición de sitio
 En primer lugar, cree el proyecto de definición de sitio en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

#### <a name="to-create-a-site-definition-project"></a>Para crear un proyecto de definición de sitio

1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**. Si el IDE está establecido para usar la configuración de desarrollo de Visual Basic, en la barra de menús, elija **archivo**  >  **nuevo proyecto**.

    Aparecerá el cuadro de diálogo **Nuevo proyecto** .

2. Expanda el nodo **Visual C#** o el **Visual Basic** , expanda el nodo **SharePoint** y, a continuación, elija el nodo **2010** .

3. En la lista de **plantillas** , elija la plantilla de **proyecto de SharePoint 2010** .

4. En el cuadro **nombre** , escriba **TestSiteDef**y elija el botón **Aceptar** .

    Aparece el **Asistente para la personalización de SharePoint** .

5. En la página **especifique el sitio y el nivel de seguridad de la depuración** , escriba la dirección URL del sitio de SharePoint en el que desea depurar la definición del sitio o use la ubicación predeterminada (<em>nombre del sistema</em>http:///).

6. En la sección **¿cuál es el nivel de confianza de esta solución de SharePoint?** , elija el botón de opción **implementar como solución de granja de servidores** .

    Todos los proyectos de definición de sitio deben implementarse como soluciones de granja. Para obtener más información sobre las soluciones en espacio aislado frente a las soluciones de granja, consulte [consideraciones sobre soluciones en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).

7. Elija el botón **Finalizar**.

    El proyecto aparece en **Explorador de soluciones**.

8. En **Explorador de soluciones**, elija el nodo del proyecto y, a continuación, en la barra de menús, elija **proyecto**  >  **Agregar nuevo elemento**.

9. En **Visual C#** o **Visual Basic**, expanda el nodo **SharePoint** y, a continuación, elija el nodo **2010** .

10. En el panel **plantillas** , elija la plantilla de **definición del sitio** , deje el **nombre** como **SiteDefinition1**y, a continuación, elija el botón **Agregar** .

## <a name="create-a-visual-web-part"></a>Crear un elemento Web Visual
 A continuación, cree un elemento Web visual para que aparezca en la Página principal de la definición del sitio.

#### <a name="to-create-a-visual-web-part"></a>Para crear un elemento Web Visual

1. En **Explorador de soluciones**, elija el botón **Mostrar todos los archivos** .

2. Elija el nodo del proyecto **SiteDefinition1** y, a continuación, en la barra de menús, elija **proyecto**  >  **Agregar nuevo elemento**.

     Aparecerá el cuadro de diálogo **Agregar nuevo elemento** .

3. Expanda el nodo **Visual C#** o el **Visual Basic** , expanda el nodo **SharePoint** y, a continuación, elija el nodo **2010** .

4. En la lista de plantillas, elija la plantilla **elemento Web visual** , conserve el nombre predeterminado VisualWebPart1 y, a continuación, elija el botón **Agregar** .

     Se abre el archivo *VisualWebPart1. ascx* .

5. En la parte inferior de *VisualWebPart1. ascx*, agregue el marcado siguiente para agregar tres controles al formulario: un cuadro de texto, un botón y una etiqueta:

    ```aspx-csharp
    <table>
      <tr>
        <td>
          <asp:TextBox runat="server" ID="tbName"></asp:TextBox>
        </td>
        <td>
          <asp:Button runat="server" ID="btnSubmit" Text = "Change Label Text" OnClick="btnSubmit_Click"></asp:Button>
        </td>
        <td>
          <asp:Label runat="server" ID="lblName"></asp:Label>
        </td>
      </tr>
    </table>
    ```

6. En *VisualWebPart1. ascx*, abra el archivo *VisualWebPart1.ascx.CS* (para [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] ) o *VisualWebPart1. ascx. VB* (para [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ) y, a continuación, agregue el código siguiente:

     [!code-vb[SP_SimpleSiteDef#1](../sharepoint/codesnippet/VisualBasic/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_SimpleSiteDef#1](../sharepoint/codesnippet/CSharp/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]

     Este código agrega funcionalidad para hacer clic en el botón del elemento Web.

## <a name="add-the-visual-web-part-to-the-default-aspx-page"></a>Agregar el elemento Web visual a la página ASPX predeterminada
 A continuación, agregue el elemento Web visual a la página ASPX predeterminada de la definición del sitio.

#### <a name="to-add-a-visual-web-part-to-the-default-aspx-page"></a>Para agregar un elemento Web visual a la página ASPX predeterminada

1. Abra la página default. aspx y, a continuación, agregue la siguiente línea en la `WebPartPages` etiqueta:

    ```aspx-csharp
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>
    ```

     Esta línea asocia el nombre MyWebPartControls al elemento Web y su código. El parámetro *namespace* coincide con el espacio de nombres que se usa en el archivo de código *VisualWebPart1. ascx* .

2. Después del `</asp:Content>` elemento, reemplace toda la `ContentPlaceHolderId="PlaceHolderMain"` sección y su contenido por el código siguiente:

    ```aspx-csharp
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">
        <MyWebPartControls:VisualWebPart1 runat="server" />
    </asp:Content>
    ```

     Este código crea una referencia al elemento Web visual que creó anteriormente.

3. En **Explorador de soluciones**, abra el menú contextual del nodo **SiteDefinition1** y, a continuación, elija **establecer como elemento de inicio**.

## <a name="deploy-and-run-the-site-definition-solution"></a>Implementación y ejecución de la solución de definición de sitio
 A continuación, implemente el proyecto en SharePoint y, a continuación, ejecute el proyecto.

#### <a name="to-deploy-and-run-the-site-definition"></a>Para implementar y ejecutar la definición de sitio

- En la barra de menús, elija **compilar**  >  **implementar TestSiteDef**.

- Elija la tecla **F5**.

     Visual Studio compila el código, agrega sus características, empaqueta todos los archivos en un archivo de solución de SharePoint (WSP) e implementa el archivo WSP en el servidor de SharePoint. Después, SharePoint instala los archivos y, a continuación, activa las características.

## <a name="create-a-site-based-on-the-site-definition"></a>Crear un sitio basado en la definición de sitio
 A continuación, cree un sitio con la nueva definición de sitio.

#### <a name="to-create-a-site-by-using-the-site-definition"></a>Para crear un sitio mediante la definición del sitio

1. En el sitio de SharePoint, aparece la página nuevo sitio de SharePoint.

2. En la sección **título y descripción** , escriba **mi nuevo sitio** para el título y una descripción del sitio.

3. En la sección **dirección del sitio web** , escriba **mynewsite** en el cuadro **nombre de dirección URL** .

4. En la sección **plantilla** , elija la pestaña **personalizaciones de SharePoint** .

5. En la lista **seleccionar una plantilla** , elija **SiteDefinition1**.

6. Deje los otros valores predeterminados y elija el botón **crear** .

     Aparece el nuevo sitio.

## <a name="test-the-new-site"></a>Probar el nuevo sitio
 A continuación, pruebe el nuevo sitio para comprobar si funciona correctamente.

#### <a name="to-test-the-new-site"></a>Para probar el nuevo sitio

- En la página ASPX predeterminada, escriba algún texto y, a continuación, elija el botón **cambiar texto de etiqueta** situado junto al cuadro de texto.

     El texto aparece en la etiqueta del lado derecho del botón.

## <a name="see-also"></a>Consulte también
- [Cómo: crear un receptor de eventos](../sharepoint/how-to-create-an-event-receiver.md)
- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
