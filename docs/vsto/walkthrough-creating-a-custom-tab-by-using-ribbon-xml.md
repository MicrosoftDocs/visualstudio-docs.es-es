---
title: 'Tutorial: Crear una pestaña personalizada usando XML de cinta de opciones'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- customizing the Ribbon, tabscustom Ribbon, tabs
- Ribbon [Office development in Visual Studio], XML
- XML [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Custom tab [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 45e35b7cf97a6b9a1f310149817f8e79956a47aa
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38808929"
---
# <a name="walkthrough-create-a-custom-tab-by-using-ribbon-xml"></a>Tutorial: Crear una pestaña personalizada usando XML de cinta de opciones
  En este tutorial se muestra cómo crear una pestaña personalizada de la cinta de opciones mediante el uso de la **cinta (XML)** elemento.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Agregar botones a la **Add-Ins** ficha. El **Add-Ins** ficha es la predeterminada que se define en el archivo XML de cinta de opciones.  
  
-   Automatizar Microsoft Office Word mediante los botones en la **Add-Ins** ficha.  
  
> [!NOTE]  
>  Es posible que el equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## <a name="create-the-project"></a>Crear el proyecto  
 El primer paso es crear un proyecto de complemento de VSTO de Word. Más adelante, personalizará la **Add-Ins** ficha de este documento.  
  
### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto  
  
1.  Crear un **complemento Word** proyecto con el nombre **MyRibbonAddIn**.  
  
     Para obtener más información, consulte [Cómo: proyectos de creación de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] se abre el **ThisAddIn.cs** o **ThisAddIn.vb** archivo de código y agrega el **MyRibbonAddIn** proyecto a **el Explorador de soluciones**.  
  
## <a name="create-the-vsto-add-ins-tab"></a>Creación de la ficha Complementos VSTO  
 Para crear el **Add-Ins** pestaña, agregue un **cinta (XML)** a su proyecto. En un paso posterior de este tutorial, agregará algunos botones a esta pestaña.  
  
### <a name="to-create-the-add-ins-tab"></a>Para crear la pestaña complementos  
  
1.  En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.  
  
2.  En el **Agregar nuevo elemento** cuadro de diálogo, seleccione **cinta (XML)**.  
  
3.  Cambie el nombre de la nueva cinta de opciones por **MyRibbon**y haga clic en **Agregar**.  
  
     El **MyRibbon.cs** o **MyRibbon.vb** archivo se abre en el diseñador. Un archivo XML que se denomina **MyRibbon.xml** también se agrega al proyecto.  
  
4.  En **el Explorador de soluciones**, haga clic en **ThisAddin.cs** o **ThisAddin.vb**y, a continuación, haga clic en **ver código**.  
  
5.  Agregue el siguiente código a la clase **ThisAddin** . Este código invalida el método `CreateRibbonExtensibilityObject` y devuelve la clase XML Ribbon a la aplicación de Office.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
6.  En **el Explorador de soluciones**, haga clic en el **MyRibbonAddIn** del proyecto y, a continuación, haga clic en **compilar**. Compruebe que el proyecto se compila sin errores.  
  
## <a name="add-buttons-to-the-add-ins-tab"></a>Agregar botones a la pestaña complementos  
 El objetivo de este complemento de VSTO es proporcionar a los usuarios una manera de agregar texto reutilizable y una tabla específica al documento activo. Para proporcionar la interfaz de usuario, agregue dos botones a la **Add-Ins** ficha modificando el archivo XML de cinta de opciones. En un paso posterior de este tutorial, definirá métodos de devolución de llamada para los botones. Para obtener más información sobre el archivo XML de cinta de opciones, consulte [Ribbon XML](../vsto/ribbon-xml.md).  
  
### <a name="to-add-buttons-to-the-add-ins-tab"></a>Para agregar botones a la pestaña complementos  
  
1.  En **el Explorador de soluciones**, haga clic en **MyRibbon.xml** y, a continuación, haga clic en **abierto**.  
  
2.  Reemplace el contenido de la **ficha** elemento con el siguiente código XML. Este código XML cambia la etiqueta del grupo de control predeterminado para **contenido**, y agrega dos nuevos botones con las etiquetas **insertar texto** y **Insertar tabla**.  
  
    ```xml  
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
  
## <a name="automate-the-document-by-using-the-buttons"></a>Automatizar el documento mediante los botones  
 Debe agregar `onAction` métodos de devolución de llamada para el **insertar texto** y **Insertar tabla** botones para realizar acciones cuando el usuario hace clic en ellos. Para obtener más información acerca de los métodos de devolución de llamada para los controles de cinta de opciones, consulte [Ribbon XML](../vsto/ribbon-xml.md).  
  
### <a name="to-add-callback-methods-for-the-buttons"></a>Para agregar métodos de devolución de llamada a los botones  
  
1.  En **el Explorador de soluciones**, haga clic en **MyRibbon.cs** o **MyRibbon.vb**y, a continuación, haga clic en **abierto**.  
  
2.  Agregue el código siguiente a la parte superior de la **MyRibbon.cs** o **MyRibbon.vb** archivo. Este código crea un alias para el espacio de nombres <xref:Microsoft.Office.Interop.Word>.  
  
     [!code-csharp[Trin_RibbonButtons#1](../vsto/codesnippet/CSharp/Trin_RibbonButtons/MyRibbon.cs#1)]
     [!code-vb[Trin_RibbonButtons#1](../vsto/codesnippet/VisualBasic/Trin_RibbonButtons/MyRibbon.vb#1)]  
  
3.  Agregue el método siguiente a la clase `MyRibbon`. Se trata de un método de devolución de llamada para el **insertar texto** botón que agrega una cadena al documento activo en la ubicación actual del cursor.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#2)]  
  
4.  Agregue el método siguiente a la clase `MyRibbon`. Se trata de un método de devolución de llamada para el **Insertar tabla** botón que agrega una tabla al documento activo en la ubicación actual del cursor.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#3)]  
  
## <a name="testing-the-vsto-add-in"></a>Probar el complemento de VSTO  
 Al ejecutar el proyecto, se abre Word y la pestaña denominada **Add-Ins** aparece en la cinta de opciones. Haga clic en el **insertar texto** y **Insertar tabla** botones en la **Add-Ins** tab para probar el código.  
  
### <a name="to-test-your-vsto-add-in"></a>Para probar el complemento de VSTO  
  
1.  Presione **F5** para ejecutar el proyecto.  
  
2.  Confirme que la **Add-Ins** pestaña está visible en la cinta de opciones.  
  
3.  Haga clic en la pestaña **Complementos** .  
  
4.  Confirme que la **contenido** grupo está visible en la cinta de opciones.  
  
5.  Haga clic en el **insertar texto** situado en la **contenido** grupo.  
  
     Se agrega una cadena al documento en la ubicación actual del cursor.  
  
6.  Haga clic en el **Insertar tabla** situado en la **contenido** grupo.  
  
     Se agrega una tabla al documento en la ubicación actual del cursor.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Puede aprender más acerca de la personalización de la interfaz de usuario de Office en estos temas:  
  
-   Personalizar la cinta de opciones de otra aplicación de Office. Para obtener más información acerca de las aplicaciones que admiten la personalización de la cinta de opciones, consulte [información general de la cinta de opciones](../vsto/ribbon-overview.md).  
  
-   Personalizar la cinta de opciones de una aplicación de Office mediante el Diseñador de cinta. Para obtener más información, consulta [Ribbon Designer](../vsto/ribbon-designer.md).  
  
-   Crear un panel de acciones personalizadas. Para obtener más información, consulte [información general sobre el panel de acciones](../vsto/actions-pane-overview.md).  
  
-   Personalizar la interfaz de usuario de Microsoft Office Outlook mediante las áreas de formulario de Outlook. Para obtener más información, consulte [Tutorial: diseñar un área de formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
## <a name="see-also"></a>Vea también  
 [Información general de la cinta de opciones](../vsto/ribbon-overview.md)   
 [XML de la cinta](../vsto/ribbon-xml.md)   
 [Tutorial: Crear una pestaña personalizada usando el Diseñador de cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  