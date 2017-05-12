---
title: "Tutorial: Crear una p&#225;gina de una aplicaci&#243;n de SharePoint"
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
  - "páginas de aplicación [desarrollo de SharePoint en Visual Studio], desarrollar"
  - "páginas de aplicación [desarrollo de SharePoint en Visual Studio], crear"
ms.assetid: 5b6dd941-5c59-4a89-89d0-8e973a00ae9e
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Tutorial: Crear una p&#225;gina de una aplicaci&#243;n de SharePoint
  Una página de aplicación es un formulario especializado de una página ASP.NET.  Las páginas de aplicación incluyen contenido que está combinado con una página maestra de SharePoint.  Para obtener más información, vea [Crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
 En este tutorial se muestra cómo crear una página de aplicación y cómo depurarla utilizando un sitio de SharePoint local.  Esta página muestra todos los elementos que cada usuario ha creado o modificado en todos los sitios de la granja de servidores.  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Crear un proyecto de SharePoint.  
  
-   Agregar una página de aplicación al proyecto de SharePoint.  
  
-   Agregar controles ASP.NET a la página de aplicación.  
  
-   Agregar código subyacente a los controles ASP.NET.  
  
-   Probar la página de aplicación.  
  
> [!NOTE]  
>  Es posible que su equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones.  La edición de Visual Studio que tenga y la configuración que esté utilizando determinan estos elementos.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de Windows y SharePoint.  Para obtener más información, vea [Requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)] o una edición de Visual Studio Ultimate o Visual Studio Premium.  
  
## Crear un proyecto de SharePoint  
 Primero, cree un **Proyecto de SharePoint vacío**.  Después, agregará un elemento **Página de aplicación** a este proyecto.  
  
#### Para crear un proyecto de SharePoint  
  
1.  Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Abra el cuadro de diálogo **Nuevo proyecto**, expanda el nodo **Office\/SharePoint** bajo el lenguaje que desea usar y, a continuación, elija el nodo **Soluciones de SharePoint**.  
  
3.  En el panel **Plantillas instaladas de Visual Studio**, elija la plantilla **SharePoint 2010 – Proyecto vacío**.  Denomine MySharePointProject al proyecto y, a continuación, elija el botón **Aceptar**.  
  
     Aparece el **Asistente para personalización de SharePoint**.  Este asistente permite seleccionar el sitio que se va a usar para depurar el proyecto, así como el nivel de confianza de la solución.  
  
4.  Elija el botón de opción **Implementar como solución de granja de servidores** y después elija el botón **Finalizar** para aceptar el sitio local predeterminado de SharePoint.  
  
## Crear una página de aplicación  
 Para crear una página de aplicación, agregue un elemento **Página de aplicación** al proyecto.  
  
#### Para crear una página de aplicación  
  
1.  En el **Explorador de soluciones**, elija el proyecto **MySharePointProject**.  
  
2.  En la barra de menús, elija **Proyecto**, **Agregar nuevo elemento**.  
  
3.  En el cuadro de diálogo de **Agregar nuevo elemento**, elija la plantilla de **Página de aplicación \(solución de granja de servidores únicamente\)**.  
  
4.  Asigne un nombre a la página SearchItems y elija el botón de **Agregar**.  
  
     El diseñador de Visual Web Developer muestra la página de aplicación en la vista **Código fuente**, donde puede ver los elementos HTML de la página.  El diseñador muestra el marcado de varios controles <xref:System.Web.UI.WebControls.Content>.  Cada control se asigna a un control <xref:System.Web.UI.WebControls.ContentPlaceHolder> que se define en la página maestra de la aplicación predeterminada.  
  
## Diseñar el diseño de la página de aplicación  
 El elemento Página de aplicación le permite utilizar un diseñador para agregar controles ASP.NET a la página de aplicación.  Este diseñador es el mismo que se utiliza en Visual Web Developer.  Agregue una etiqueta, una lista de botones de radio y una tabla a la vista **Código fuente** del diseñador y, a continuación, establezca las propiedades como lo haría cuando diseña cualquier página ASP.NET estándar.  
  
 Para obtener más información sobre el uso del diseñador en Visual Web Developer, vea [Mapa de contenido del entorno de desarrollo web de Visual Studio](http://msdn.microsoft.com/es-es/9c31f93b-c8fb-4599-9b14-6194ec8c7539).  
  
#### Para diseñar el diseño de la página de aplicación  
  
1.  En la barra de menús, elija **Ver**, **Cuadro de herramientas**.  
  
2.  En el nodo estándar de **Cuadro de herramientas**, realice uno de los pasos siguientes:  
  
    -   Abra el menú contextual para el elemento de **Etiqueta**, elija **Copia**, abra el menú contextual para la línea bajo control de contenido de **PlaceHolderMain** en el diseñador y, a continuación, elija **Pegar**.  
  
    -   Arrastre el elemento **Etiqueta** desde **Cuadro de herramientas** hasta el cuerpo del control de contenido **PlaceHolderMain**.  
  
3.  Repita el paso anterior para agregar un elemento de **DropDownList** y un elemento de **Table** al control de contenido de **PlaceHolderMain**.  
  
4.  En el diseñador, cambie el valor del atributo `Text` del control de etiqueta por Mostrar todos los elementos.  
  
5.  En el diseñador, reemplace el elemento `<asp:DropDownList>` por el XML siguiente.  
  
    ```  
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"  
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">  
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>  
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>  
    </asp:DropDownList>  
    ```  
  
## Controlar los eventos de los controles en la página  
 Controle los controles de una página de aplicación como lo haría en una página ASP.NET.  En este procedimiento controlará el evento `SelectedIndexChanged` de la lista desplegable.  
  
#### Para controlar los eventos de los controles en la página  
  
1.  En el menú **Ver**, elija **Código**.  
  
     El archivo de código de la página de aplicación se abre en el editor de código.  
  
2.  Agregue el método siguiente a la clase `SearchItems`.  Este código controla el evento <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged> de <xref:System.Web.UI.WebControls.DropDownList> llamando a un método que creará posteriormente en este tutorial.  
  
     [!code-csharp[SP_ApplicationPage#5](../snippets/csharp/VS_Snippets_OfficeSP/sp_applicationpage/cs/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]
     [!code-vb[SP_ApplicationPage#5](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_applicationpage/vb/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]  
  
3.  Agregue las siguientes instrucciones a la parte superior del archivo de código de la página de aplicación.  
  
     [!code-csharp[SP_ApplicationPage#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_applicationpage/cs/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]
     [!code-vb[SP_ApplicationPage#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_applicationpage/vb/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]  
  
4.  Agregue el método siguiente a la clase `SearchItems`.  Este método recorre en iteración todos los sitios de la granja de servidores y busca los elementos creados o modificados por el usuario actual.  
  
     [!code-csharp[SP_ApplicationPage#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_applicationpage/cs/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]
     [!code-vb[SP_ApplicationPage#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_applicationpage/vb/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]  
  
5.  Agregue el método siguiente a la clase `SearchItems`.  Este método muestra elementos creados o modificados por el usuario actual en la tabla.  
  
     [!code-csharp[SP_ApplicationPage#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_applicationpage/cs/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]
     [!code-vb[SP_ApplicationPage#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_applicationpage/vb/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]  
  
## Probar la página de aplicación  
 Al ejecutar el proyecto, se abre el sitio de SharePoint y aparece la página de aplicación.  
  
#### Para probar la página de aplicación  
  
1.  En el **Explorador de soluciones**, abra el menú contextual para la página de la aplicación y elija **Establecer como elemento de inicio**.  
  
2.  Elija la tecla F5.  
  
     Se abre el sitio de SharePoint.  
  
3.  En la página de aplicación, elija la opción **Modificado por mí**.  
  
     La página de aplicación se actualiza y muestra todos los elementos que ha modificado en todos los sitios de la granja de servidores.  
  
4.  En la página de aplicación, elija **Creados por mí** en la lista.  
  
     La página de aplicación se actualiza y muestra todos los elementos que ha creado en todos los sitios de la granja de servidores.  
  
## Pasos siguientes  
 Para obtener más información sobre las páginas de aplicación de SharePoint, vea [Crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
 En los temas siguientes puede obtener más información sobre cómo diseñar el contenido de páginas de SharePoint con Visual Web Designer:  
  
-   [Crear elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
-   [Crear controles reutilizables para elementos web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
## Vea también  
 [Cómo: Crear una página de aplicación](../sharepoint/how-to-create-an-application-page.md)   
 [Tipo de aplicación de página \_layouts](http://go.microsoft.com/fwlink/?LinkID=169274)  
  
  