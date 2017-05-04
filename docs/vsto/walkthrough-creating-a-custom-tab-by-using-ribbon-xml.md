---
title: "Tutorial: Crear una pesta&#241;a personalizada usando XML de la cinta de opciones | Microsoft Docs"
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
  - "pestaña personalizada [desarrollo de Office en Visual Studio]"
  - "personalizar la cinta de opciones, Cinta personalizada con pestañas, pestañas"
  - "Cinta [desarrollo de Office en Visual Studio], personalizar"
  - "Cinta [desarrollo de Office en Visual Studio], pestañas"
  - "Cinta [desarrollo de Office en Visual Studio], XML"
  - "XML [desarrollo de Office en Visual Studio], cinta de opciones"
ms.assetid: f6391a01-df1a-4a0f-bfbb-a9526c73b2b3
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# Tutorial: Crear una pesta&#241;a personalizada usando XML de la cinta de opciones
  En este tutorial se muestra cómo crear una pestaña personalizada de la cinta de opciones mediante el elemento **Cinta \(XML\)**.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Agregar botones a la pestaña **Complementos**.  La pestaña **Complementos** es la pestaña predeterminada que se define en el archivo XML de la cinta de opciones.  
  
-   Automatizar Microsoft Office Word mediante los botones de la pestaña **Complementos**.  
  
> [!NOTE]  
>  Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones.  La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos.  Para obtener más información, consulte [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## Crear el proyecto  
 El primer paso es crear un proyecto de complemento de VSTO de Word.  Más adelante, personalizará la pestaña **Complementos** de este documento.  
  
#### Para crear un nuevo proyecto  
  
1.  Cree un proyecto de **complemento de Word** con el nombre MyRibbonAddIn.  
  
     Para obtener más información, consulte [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] abre el archivo de código **ThisAddIn.cs** o **ThisAddIn.vb** y agrega el proyecto **MyRibbonAddIn** al **Explorador de soluciones**.  
  
## Crear la pestaña Complementos de VSTO  
 Para crear la pestaña **Complementos**, agregue un elemento **Cinta \(XML\)** al proyecto.  En un paso posterior de este tutorial, agregará algunos botones a esta pestaña.  
  
#### Para crear la pestaña Complementos  
  
1.  En el menú **Proyecto**, haga clic en **Agregar nuevo elemento**.  
  
2.  En el cuadro de diálogo **Agregar nuevo elemento**, seleccione **Cinta \(XML\)**.  
  
3.  Cambie el nombre de la nueva cinta de opciones por **MyRibbon** y haga clic en **Agregar**.  
  
     El archivo **MyRibbon.cs** o **MyRibbon.vb** se abre en el diseñador.  También se agrega al proyecto un archivo XML llamado **MyRibbon.xml**.  
  
4.  En el **Explorador de soluciones**, haga clic con el botón derecho en el archivo **ThisAddin.cs** o **ThisAddin.vb** y, después, haga clic en **Ver código**.  
  
5.  Agregue el siguiente código a la clase **ThisAddin**.  Este código invalida el método CreateRibbonExtensibilityObject y devuelve la clase XML Ribbon a la aplicación de Office.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/VB/ThisAddIn.vb#1)]  
  
6.  En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto **MyRibbonAddIn** y, después, haga clic en **Compilar**.  Compruebe que el proyecto se compila sin errores.  
  
## Agregar botones a la pestaña Complementos  
 El objetivo de este complemento de VSTO es proporcionar a los usuarios una manera de agregar texto reutilizable y una tabla específica al documento activo.  Para proporcionar la interfaz de usuario, agregue dos botones a la pestaña **Complementos** modificando el archivo XML de la cinta de opciones.  En un paso posterior de este tutorial, definirá métodos de devolución de llamada para los botones.  Para obtener más información sobre el archivo XML de la cinta de opciones, consulte [XML de la cinta de opciones](../vsto/ribbon-xml.md).  
  
#### Para agregar botones a la pestaña Complementos  
  
1.  En el **Explorador de soluciones**, haga clic con el botón derecho en **MyRibbon.xml** y, después, haga clic en **Abrir**.  
  
2.  Reemplace el contenido del elemento **tab** por el siguiente código XML.  Este código XML cambia la etiqueta del grupo de control predeterminado por **Contenido** y agrega dos botones nuevos con las etiquetas **Insertar texto** e **Insertar tabla**.  
  
    ```  
    <tab idMso="TabAddIns">  
        <group id="ContentGroup" label="Content">  
            <button id="textButton" label="Insert Text"  
                 screentip="Text" onAction="OnTextButton"  
                 supertip="Inserts text at the cursor location."/>  
            <button id="tableButton" label="Insert Table"  
                 screentip="Table" onAction="OnTableButton"  
                 supertip="Inserts a table at the cursor location."/>  
        </group>  
    </tab>  
    ```  
  
## Automatizar el documento mediante los botones  
 Debe agregar métodos de devolución de llamada `onAction` para que los botones **Insertar texto** e **Insertar tabla** lleven a cabo acciones cuando el usuario hace clic en ellos.  Para obtener más información sobre los métodos de devolución de llamada de los controles de la cinta de opciones, consulte [XML de la cinta de opciones](../vsto/ribbon-xml.md).  
  
#### Para agregar métodos de devolución de llamada a los botones  
  
1.  En el **Explorador de soluciones**, haga clic con el botón derecho en **MyRibbon.cs** o **MyRibbon.vb** y, después, haga clic en **Abrir**.  
  
2.  Agregue el siguiente código a la parte superior del archivo **MyRibbon.cs** o **MyRibbon.vb**.  Este código crea un alias para el espacio de nombres <xref:Microsoft.Office.Interop.Word>.  
  
     [!code-csharp[Trin_RibbonButtons#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_RibbonButtons/CS/MyRibbon.cs#1)]
     [!code-vb[Trin_RibbonButtons#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_RibbonButtons/VB/MyRibbon.vb#1)]  
  
3.  Agregue el método siguiente a la clase `MyRibbon`.  Se trata de un método de devolución de llamada para el botón **Insertar texto** que agrega una cadena al documento activo en la ubicación actual del cursor.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/CS/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/VB/MyRibbon.vb#2)]  
  
4.  Agregue el método siguiente a la clase `MyRibbon`.  Se trata de un método de devolución de llamada para el botón **Insertar tabla** que agrega una tabla al documento activo en la ubicación actual del cursor.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/CS/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/VB/MyRibbon.vb#3)]  
  
## Probar el complemento de VSTO  
 Al ejecutar el proyecto, se abre Word y aparece la pestaña **Complementos** en la cinta de opciones.  Haga clic en los botones **Insertar texto** e **Insertar tabla** de la pestaña **Complementos** para probar el código.  
  
#### Para probar el complemento de VSTO  
  
1.  Presione F5 para ejecutar el proyecto.  
  
2.  Confirme que la pestaña **Complementos** está visible en la cinta de opciones.  
  
3.  Haga clic en la pestaña **Complementos**.  
  
4.  Confirme que el grupo **Contenido** está visible en la cinta de opciones.  
  
5.  Haga clic en el botón **Insertar texto** del grupo **Contenido**.  
  
     Se agrega una cadena al documento en la ubicación actual del cursor.  
  
6.  Haga clic en el botón **Insertar tabla** del grupo **Contenido**.  
  
     Se agrega una tabla al documento en la ubicación actual del cursor.  
  
## Pasos siguientes  
 Puede aprender más acerca de la personalización de la interfaz de usuario de Office en estos temas:  
  
-   Personalizar la cinta de opciones de otra aplicación de Office.  Para obtener más información sobre las aplicaciones que admiten la personalización de la cinta de opciones, consulte [Información general sobre la cinta de opciones](../vsto/ribbon-overview.md).  
  
-   Personalizar la cinta de opciones de una aplicación de Office mediante el Diseñador de la cinta de opciones.  Para obtener más información, consulte [Diseñador de la cinta de opciones](../vsto/ribbon-designer.md).  
  
-   Crear un panel de acciones personalizadas.  Para obtener más información, consulte [Información general sobre paneles de acciones](../vsto/actions-pane-overview.md).  
  
-   Personalizar la interfaz de usuario de Microsoft Office Outlook mediante las áreas de formulario de Outlook.  Para obtener más información, consulte [Tutorial: Diseñar un área de formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
## Vea también  
 [Información general sobre la cinta de opciones](../vsto/ribbon-overview.md)   
 [XML de la cinta de opciones](../vsto/ribbon-xml.md)   
 [Tutorial: Crear una pestaña personalizada usando el diseñador de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  