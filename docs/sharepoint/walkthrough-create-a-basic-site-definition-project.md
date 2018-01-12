---
title: "Tutorial: Crear un proyecto de definición de sitio básico | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 72a99a082fb1626013be6fa0ac5c759a43fd58a7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-create-a-basic-site-definition-project"></a>Tutorial: Crear un proyecto de definición de sitio básico
  En este tutorial se muestra cómo crear una definición de sitio básico que contiene un elemento Web visual con algunos controles en él. Por razones de claridad, el elemento Web visual que creas tiene solo algunos controles. Sin embargo, puede crear definiciones de sitio de SharePoint más sofisticadas que incluyen más funcionalidad.  
  
 En este tutorial se muestran las siguientes tareas:  
  
-   Crear una definición de sitio mediante la [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] plantilla de proyecto.  
  
-   Crear un sitio de SharePoint mediante una definición de sitio de SharePoint.  
  
-   Agregar un elemento Web visual a la solución.  
  
-   Al agregar el nuevo elemento Web visual a la se puede personalizar la página del sitio default.aspx.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de Microsoft Windows y SharePoint. Para obtener más información, vea Requisitos para desarrollar soluciones de SharePoint.  
  
-   Visual Studio.  
  
## <a name="creating-a-site-definition-solution"></a>Crear una solución de definición de sitio  
 En primer lugar, cree el proyecto de definición de sitio en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### <a name="to-create-a-site-definition-project"></a>Para crear un proyecto de definición de sitio  
  
1.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**. Si su IDE está configurado para usar la configuración de desarrollo de Visual Basic, en la barra de menús, elija **archivo**, **nuevo proyecto**.  
  
     Aparecerá el cuadro de diálogo **Nuevo proyecto** .  
  
2.  Expanda el **Visual C#** nodo o la **Visual Basic** nodo, expanda el **SharePoint** nodo y, a continuación, elija la **2010** nodo.  
  
3.  En el **plantillas** lista, elija la **proyecto de SharePoint 2010** plantilla.  
  
4.  En el **nombre** cuadro, escriba **TestSiteDef**y, a continuación, elija la **Aceptar** botón.  
  
     El **Asistente para personalización de SharePoint** aparece.  
  
5.  En el **especificar el nivel de sitio y la seguridad para la depuración** página, escriba la dirección URL del sitio de SharePoint donde desea depurar la definición de sitio o utilice la ubicación predeterminada (http://*nombre del sistema*/).  
  
6.  En el **¿qué es el nivel de confianza para esta solución de SharePoint?** sección, elija el **implementar como solución de granja de servidores** botón de opción.  
  
     Todos los proyectos de definición de sitio se deben implementar como soluciones de granja de servidores. Para obtener más información acerca de las soluciones en espacio aislado frente a soluciones de granja de servidores, consulte [consideraciones sobre la solución en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Elija la **finalizar** botón.  
  
     El proyecto aparece en **el Explorador de soluciones**.  
  
8.  En **el Explorador de soluciones**, elija el nodo del proyecto y, a continuación, en la barra de menús, elija **proyecto**, **Agregar nuevo elemento**.  
  
9. Bajo **Visual C#** o **Visual Basic**, expanda la **SharePoint** nodo y, a continuación, elija la **2010** nodo.  
  
10. En el **plantillas** panel, elija la **definición de sitio** plantilla, deje la **nombre** como **SiteDefinition1**y, a continuación, elija la  **Agregar** botón.  
  
## <a name="create-a-visual-web-part"></a>Crear un elemento Web Visual  
 A continuación, cree un elemento Web visual para que aparezcan en la página principal de la definición sitio.  
  
#### <a name="to-create-a-visual-web-part"></a>Para crear un elemento Web visual  
  
1.  En **el Explorador de soluciones**, elija la **mostrar todos los archivos** botón.  
  
2.  Elija la **SiteDefinition1** nodo de proyecto y, a continuación, en la barra de menús, elija **proyecto**, **Agregar nuevo elemento**.  
  
     Aparecerá el cuadro de diálogo **Agregar nuevo elemento**.  
  
3.  Expanda el **Visual C#** nodo o la **Visual Basic** nodo, expanda el **SharePoint** nodo y, a continuación, elija la **2010** nodo.  
  
4.  En la lista de plantillas, elija la **elemento Web Visual** plantilla, mantener el valor predeterminado nombre VisualWebPart1 y, a continuación, elija la **agregar** botón.  
  
     Abre el archivo VisualWebPart1.ascx.  
  
5.  En la parte inferior de VisualWebPart1.ascx, agregue el marcado siguiente para agregar tres controles al formulario: un cuadro de texto, un botón y una etiqueta:  
  
    ```  
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
  
6.  En VisualWebPart1.ascx, abra el archivo VisualWebPart1.ascx.cs (para [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]) o VisualWebPart1.ascx.vb (para [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) y, a continuación, agregue el código siguiente:  
  
     [!code-vb[SP_SimpleSiteDef#1](../sharepoint/codesnippet/VisualBasic/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_SimpleSiteDef#1](../sharepoint/codesnippet/CSharp/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]  
  
     Este código agrega funcionalidad de clic de botón del elemento web.  
  
## <a name="add-the-visual-web-part-to-the-default-aspx-page"></a>Agregar el elemento Web Visual a la página ASPX predeterminada  
 A continuación, agregar el elemento Web visual a la página ASPX de la definición de sitio predeterminado.  
  
#### <a name="to-add-a-visual-web-part-to-the-default-aspx-page"></a>Para agregar un elemento Web visual a la página ASPX predeterminada  
  
1.  Abra la página default.aspx y, a continuación, agregue la siguiente línea en la `WebPartPages` etiqueta:  
  
    ```  
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>  
    ```  
  
     Esta línea asocia el nombre MyWebPartControls con el elemento Web y su código. El *Namespace* parámetro coincide con el espacio de nombres que se utiliza en el archivo de código VisualWebPart1.ascx.  
  
2.  Después de la `</asp:Content>` elemento, reemplace todo el `ContentPlaceHolderId="PlaceHolderMain"` sección y su contenido con el código siguiente:  
  
    ```  
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">  
        <MyWebPartControls:VisualWebPart1 runat="server" />      
    </asp:Content>  
    ```  
  
     Este código crea una referencia al elemento Web visual en el que creó anteriormente.  
  
3.  En **el Explorador de soluciones**, abra el menú contextual para el **SiteDefinition1** nodo y, a continuación, elija **establecer como elemento de inicio**.  
  
## <a name="deploy-and-run-the-site-definition-solution"></a>Implementar y ejecutar la solución de definición de sitio  
 A continuación, implementará el proyecto en SharePoint y, a continuación, ejecute el proyecto.  
  
#### <a name="to-deploy-and-run-the-site-definition"></a>Para implementar y ejecutar la definición de sitio  
  
-   En la barra de menús, elija **generar**, **TestSiteDef implementar**.  
  
-   Elija la tecla F5.  
  
     Visual Studio compila el código, agrega sus características, empaqueta todos los archivos en un archivo de solución (WSP) de SharePoint e implementa el archivo WSP en SharePoint Server. SharePoint, a continuación, instala los archivos y, a continuación, activa las características.  
  
## <a name="create-a-site-based-on-the-site-definition"></a>Crear un sitio basado en la definición de sitio  
 A continuación, crear un sitio mediante la nueva definición de sitio.  
  
#### <a name="to-create-a-site-by-using-the-site-definition"></a>Para crear un sitio mediante la definición de sitio  
  
1.  En el sitio de SharePoint, aparece la página nuevo sitio de SharePoint.  
  
2.  En el **título y descripción** sección, escriba **mi nuevo sitio** para el título y una descripción del sitio.  
  
3.  En el **dirección del sitio Web** sección, escriba **miNuevoSitio** en el **nombre de dirección URL** cuadro.  
  
4.  En el **plantilla** sección, elija el **personalizaciones de SharePoint** ficha.  
  
5.  En el **seleccione una plantilla de** elija **SiteDefinition1**.  
  
6.  Deje los otros valores en sus valores predeterminados y, a continuación, elija la **crear** botón.  
  
     Aparece el nuevo sitio.  
  
## <a name="test-the-new-site"></a>Probar el nuevo sitio  
 A continuación, pruebe el nuevo sitio para comprobar si funciona correctamente.  
  
#### <a name="to-test-the-new-site"></a>Para probar el nuevo sitio  
  
-   En la página ASPX predeterminada, escriba algún texto y, a continuación, elija la **texto de la etiqueta de cambio** situado junto al cuadro de texto.  
  
     El texto aparece en la etiqueta a la derecha del botón.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: crear un receptor de eventos](../sharepoint/how-to-create-an-event-receiver.md)   
 [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  