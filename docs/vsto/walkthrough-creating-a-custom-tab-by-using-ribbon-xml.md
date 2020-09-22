---
title: 'Tutorial: crear una pestaña personalizada usando XML de la cinta de opciones'
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e05bd9173b83ec3303a058dcf61ea48a7ef7675c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842451"
---
# <a name="walkthrough-create-a-custom-tab-by-using-ribbon-xml"></a>Tutorial: crear una pestaña personalizada usando XML de la cinta de opciones
  En este tutorial se muestra cómo crear una pestaña personalizada de la cinta de opciones mediante el elemento **cinta (XML)** .

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 En este tutorial se muestran las tareas siguientes:

- Agregar botones a la pestaña **Complementos** . La pestaña **Complementos** es la pestaña predeterminada que se define en el archivo XML de la cinta de opciones.

- Automatizar Microsoft Office Word mediante los botones de la pestaña **Complementos** .

> [!NOTE]
> Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-the-project"></a>Crear el proyecto
 El primer paso es crear un proyecto de complemento de VSTO de Word. Más adelante se personalizará la pestaña **Complementos** de este documento.

### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto

1. Cree un proyecto de **complemento de Word** con el nombre **MyRibbonAddIn**.

     Para obtener más información, vea [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] abre el archivo de código **ThisAddIn.CS** o **ThisAddIn. VB** y agrega el proyecto **MyRibbonAddIn** a **Explorador de soluciones**.

## <a name="create-the-vsto-add-ins-tab"></a>Crear la pestaña complementos de VSTO
 Para crear la pestaña **Complementos** , agregue un elemento **cinta (XML)** al proyecto. En un paso posterior de este tutorial, agregará algunos botones a esta pestaña.

### <a name="to-create-the-add-ins-tab"></a>Para crear la pestaña complementos

1. En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.

2. En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **cinta (XML)**.

3. Cambie el nombre de la nueva cinta de opciones por **MyRibbon**y haga clic en **Agregar**.

     Se abre el archivo **MyRibbon.CS** o **myribbon. VB** en el diseñador. También se agregará a su proyecto un archivo XML denominado **MyRibbon.xml** .

4. En **Explorador de soluciones**, haga clic con el botón secundario en **ThisAddIn.CS** o **ThisAddIn. VB**y, a continuación, haga clic en **Ver código**.

5. Agregue el siguiente código a la clase **ThisAddin** . Este código invalida el método `CreateRibbonExtensibilityObject` y devuelve la clase XML Ribbon a la aplicación de Office.

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]

6. En **Explorador de soluciones**, haga clic con el botón secundario en el proyecto **MyRibbonAddIn** y, a continuación, haga clic en **compilar**. Compruebe que el proyecto se compila sin errores.

## <a name="add-buttons-to-the-add-ins-tab"></a>Agregar botones a la pestaña complementos
 El objetivo de este complemento de VSTO es proporcionar a los usuarios una manera de agregar texto reutilizable y una tabla específica al documento activo. Para proporcionar la interfaz de usuario, agregue dos botones a **la pestaña** complementos modificando el archivo XML de la cinta de opciones. En un paso posterior de este tutorial, definirá métodos de devolución de llamada para los botones. Para obtener más información sobre el archivo XML de la cinta de opciones, vea XML de la [cinta](../vsto/ribbon-xml.md).

### <a name="to-add-buttons-to-the-add-ins-tab"></a>Para agregar botones a la pestaña complementos

1. En **Explorador de soluciones**, haga clic con el botón secundario en **MyRibbon.xml** y haga clic en **abrir**.

2. Reemplace el contenido del elemento **Tab** por el siguiente código XML. Este XML cambia la etiqueta del grupo de control predeterminado a **contenido**y agrega dos nuevos botones con las etiquetas **insertar texto** e **Insertar tabla**.

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

## <a name="automate-the-document-by-using-the-buttons"></a>Automatizar el documento mediante el uso de los botones
 Debe agregar `onAction` métodos de devolución de llamada para que los botones **insertar texto** e **Insertar tabla** realicen acciones cuando el usuario haga clic en ellos. Para obtener más información sobre los métodos de devolución de llamada para los controles de la cinta, vea [XML de la cinta](../vsto/ribbon-xml.md).

### <a name="to-add-callback-methods-for-the-buttons"></a>Para agregar métodos de devolución de llamada a los botones

1. En **Explorador de soluciones**, haga clic con el botón secundario en **MyRibbon.CS** o **myribbon. VB**y, a continuación, haga clic en **abrir**.

2. Agregue el código siguiente en la parte superior del archivo **MyRibbon.CS** o **myribbon. VB** . Este código crea un alias para el espacio de nombres <xref:Microsoft.Office.Interop.Word>.

     [!code-csharp[Trin_RibbonButtons#1](../vsto/codesnippet/CSharp/Trin_RibbonButtons/MyRibbon.cs#1)]
     [!code-vb[Trin_RibbonButtons#1](../vsto/codesnippet/VisualBasic/Trin_RibbonButtons/MyRibbon.vb#1)]

3. Agregue el siguiente método a la clase `MyRibbon`. Se trata de un método de devolución de llamada para el botón **insertar texto** que agrega una cadena al documento activo en la ubicación actual del cursor.

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#2)]

4. Agregue el siguiente método a la clase `MyRibbon`. Se trata de un método de devolución de llamada para el botón **Insertar tabla** que agrega una tabla al documento activo en la ubicación actual del cursor.

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#3)]

## <a name="testing-the-vsto-add-in"></a>Probar el complemento de VSTO
 Al ejecutar el proyecto, se abre Word y aparece la pestaña **Complementos** denominados en la cinta de opciones. Haga clic en los botones **insertar texto** e **Insertar tabla** en la pestaña **Complementos** para probar el código.

### <a name="to-test-your-vsto-add-in"></a>Para probar el complemento de VSTO

1. Presione **F5** para ejecutar el proyecto.

2. Confirme que la pestaña **Complementos** está visible en la cinta de opciones.

3. Haga clic en la pestaña **Complementos** .

4. Confirme que el grupo de **contenido** está visible en la cinta de opciones.

5. Haga clic en el botón **insertar texto** del grupo **contenido** .

     Se agrega una cadena al documento en la ubicación actual del cursor.

6. Haga clic en el botón **Insertar tabla** del grupo **contenido** .

     Se agrega una tabla al documento en la ubicación actual del cursor.

## <a name="next-steps"></a>Pasos siguientes
 Puede aprender más acerca de la personalización de la interfaz de usuario de Office en estos temas:

- Personalizar la cinta de opciones de una aplicación de Office diferente. Para obtener más información sobre las aplicaciones que admiten la personalización de la cinta de opciones, consulte [información general](../vsto/ribbon-overview.md)sobre la cinta.

- Personalizar la cinta de opciones de una aplicación de Office mediante el diseñador de la cinta de opciones. Para obtener más información, consulta [Ribbon Designer](../vsto/ribbon-designer.md).

- Crear un panel de acciones personalizadas. Para obtener más información, vea [información general del panel de acciones](../vsto/actions-pane-overview.md).

- Personalizar la interfaz de usuario de Microsoft Office Outlook mediante las áreas de formulario de Outlook. Para obtener más información, vea [Tutorial: diseñar un área de formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).

## <a name="see-also"></a>Vea también
- [Información general sobre la cinta](../vsto/ribbon-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Tutorial: crear una pestaña personalizada mediante el diseñador de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
