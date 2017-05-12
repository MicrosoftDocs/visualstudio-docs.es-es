---
title: "Tutorial: Crear un proyecto de definici&#243;n de sitio b&#225;sico"
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
  - "desarrollo de SharePoint en Visual Studio, definiciones de sitio"
  - "definiciones de sitio [desarrollo de SharePoint en Visual Studio]"
ms.assetid: b0df5b0e-5fa0-43d8-a339-6d92f1276764
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# Tutorial: Crear un proyecto de definici&#243;n de sitio b&#225;sico
  En este tutorial se muestra cómo crear una definición de sitio básica que contenga un elemento web visual con algunos controles.  Por razones de claridad, el elemento web visual que va a crear tiene pocos controles.  Sin embargo, puede crear definiciones de sitio de SharePoint más sofisticadas con más funcionalidad.  
  
 En este tutorial se muestran las siguientes tareas:  
  
-   Crear una definición de sitio utilizando la plantilla de proyecto de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   Crear un sitio de SharePoint utilizando una definición de sitio en SharePoint.  
  
-   Agregar un elemento web visual a la solución.  
  
-   Personalizar la página default.aspx del sitio agregándole el nuevo elemento web visual.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de Microsoft Windows y SharePoint.  Para obtener más información, vea Requisitos para desarrollar soluciones de SharePoint.  
  
-   Visual Studio.  
  
## Crear una solución de definición de sitio  
 Primero, cree el proyecto de definición de sitio en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### Para crear un proyecto de definición de sitio  
  
1.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  Si el IDE está establecido para utilizar la configuración de desarrollo de Visual Basic, en la barra de menú, elija **archivo**, **Nuevo proyecto**.  
  
     Aparece el cuadro de diálogo **Nuevo proyecto**.  
  
2.  Expanda el nodo de **Visual C\#** o el nodo de **Visual Basic** , expanda el nodo de **sharepoint** y, a continuación el nodo de **2010** .  
  
3.  En la lista de **Plantillas** , elija la plantilla de **SharePoint 2010 Project** .  
  
4.  En el cuadro de **Name** , entre en TestSiteDef, y elija el botón de **Aceptar** .  
  
     Aparece el **Asistente para personalización de SharePoint**.  
  
5.  En la página de **Especifique el sitio y el nivel de seguridad de la depuración** , escriba la dirección URL del sitio de SharePoint donde desea depurar la definición de sitio, o utilice la ubicación predeterminada \(http:\/\/*System Name*\/\).  
  
6.  En la sección **¿Cuál es el nivel de confianza de esta solución de SharePoint?**, elija el botón de opción **Implementar como solución de granja de servidores**.  
  
     Todos los proyectos de definición de sitio se deben implementar como soluciones de granja.  Para obtener más información sobre soluciones de granja y soluciones en espacio aislado, vea [Consideraciones sobre las soluciones en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Elija el botón **Finalizar**.  
  
     El proyecto aparecerá en el **Explorador de soluciones**.  
  
8.  En **Explorador de soluciones**, elija el nodo de proyecto y, a continuación, en la barra de menús, elija **Project**, **Agregar nuevo elemento**.  
  
9. En **Visual C\#** o **Visual Basic**, expanda el nodo de **sharepoint** y, a continuación el nodo de **2010** .  
  
10. En el panel de **Plantillas** , elija la plantilla de **Definición de sitio** , deje **Name** como **SiteDefinition1**, y elija el botón de **Add** .  
  
## Crear un elemento web visual  
 A continuación, cree un elemento web visual que aparecerá en la página principal de la definición de sitio.  
  
#### Para crear un elemento web visual  
  
1.  En **Explorador de soluciones**, elija el botón de **Mostrar todos los archivos** .  
  
2.  Elija el nodo del proyecto de **SiteDefinition1** y, a continuación, en la barra de menú, elija **Project**, **Agregar nuevo elemento**.  
  
     Aparecerá el cuadro de diálogo **Agregar nuevo elemento**.  
  
3.  Expanda el nodo de **Visual C\#** o el nodo de **Visual Basic** , expanda el nodo de **sharepoint** y, a continuación el nodo de **2010** .  
  
4.  En la lista de plantillas, elija la plantilla de **Elemento web visual** , mantenga el nombre predeterminado VisualWebPart1, y elija el botón de **Add** .  
  
     El archivo de VisualWebPart1.ascx abra.  
  
5.  En la parte inferior de VisualWebPart1.ascx, agregue el marcado siguiente para agregar tres controles al formulario: un cuadro de texto, un botón, y una etiqueta:  
  
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
  
6.  En VisualWebPart1.ascx, abra el archivo de VisualWebPart1.ascx.cs \(para [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]\) o VisualWebPart1.ascx.vb \(para [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\), y después agregue el código siguiente:  
  
     [!code-csharp[SP_SimpleSiteDef#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_simplesitedef/cs/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]
     [!code-vb[SP_SimpleSiteDef#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_simplesitedef/vb/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]  
  
     Este código agrega la funcionalidad para el clic de botón del elemento web.  
  
## Agregar el elemento web visual a la página ASPX predeterminada  
 A continuación, agregue el elemento web visual a la página ASPX predeterminada de la definición del sitio.  
  
#### Para agregar el elemento web visual a la página ASPX predeterminada  
  
1.  Abra la página default.aspx y, a continuación la línea siguiente bajo la etiqueta de `WebPartPages` :  
  
    ```  
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>  
    ```  
  
     Esta línea asocia el nombre MyWebPartControls al elemento web y su código.  Coincide con el parámetro de *Namespace* el espacio de nombres que se utiliza en el archivo de código de VisualWebPart1.ascx.  
  
2.  Después del elemento de `</asp:Content>` , reemplace la sección completa de `ContentPlaceHolderId="PlaceHolderMain"` y su contenido por el código siguiente:  
  
    ```  
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">  
        <MyWebPartControls:VisualWebPart1 runat="server" />      
    </asp:Content>  
    ```  
  
     Este código crea una referencia al elemento web visual anteriormente creado.  
  
3.  En **Explorador de soluciones**, abra el menú contextual para el nodo de **SiteDefinition1** y, a continuación **Conjunto como elemento de inicio**.  
  
## Implementar y ejecutar la solución de definición de sitio  
 A continuación, implemente el proyecto en SharePoint, y después ejecute el proyecto.  
  
#### Para implementar y ejecutar la definición de sitio  
  
-   En la barra de menú, elija **Compilación**, **Implemente TestSiteDef**.  
  
-   Elija la tecla F5.  
  
     Visual Studio compila el código, agrega sus características, empaqueta todos los archivos en un archivo de solución de SharePoint \(WSP\), e implementa el archivo WSP en el Servidor de SharePoint.  A continuación, SharePoint instala los archivos y después activa las características.  
  
## Crear un sitio basado en la definición de sitio  
 A continuación cree un sitio utilizando la nueva definición de sitio.  
  
#### Para crear un sitio utilizando la definición de sitio  
  
1.  En el sitio de SharePoint, aparece la página Nuevo sitio de SharePoint.  
  
2.  En la sección **Título y descripción**, escriba Nuevo sitio como título y una descripción del sitio.  
  
3.  En la sección **Dirección de sitio web**, escriba nuevositio en el cuadro **Nombre de URL**.  
  
4.  En la sección de **Plantilla** , elija la ficha de **Personalizaciones de SharePoint** .  
  
5.  En la lista de **Seleccionar una plantilla** , elija **SiteDefinition1**.  
  
6.  Deje los otros valores en sus valores predeterminados, y elija el botón de **crear** .  
  
     Aparecerá el nuevo sitio.  
  
## Probar el nuevo sitio  
 A continuación, pruebe el nuevo sitio para comprobar si funciona correctamente.  
  
#### Para probar el nuevo sitio  
  
-   En la página ASPX predeterminada, escriba texto, y elija el botón de **Texto de la etiqueta de cambio** junto al cuadro.  
  
     El texto aparece en la etiqueta a la derecha del botón.  
  
## Vea también  
 [Cómo: Crear un receptor de eventos](../sharepoint/how-to-create-an-event-receiver.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  