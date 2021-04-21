---
title: 'Tutorial: Creación de una pestaña personalizada mediante XML de la cinta de opciones'
description: Obtenga información sobre cómo agregar botones a la Add-Ins y automatizar Microsoft Word mediante la cinta de opciones (XML).
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a5d7992462ac3ece9782b0168feedd87577c2d0e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826335"
---
# <a name="walkthrough-create-a-custom-tab-by-using-ribbon-xml"></a>Tutorial: Creación de una pestaña personalizada mediante XML de la cinta de opciones
  En este tutorial se muestra cómo crear una pestaña personalizada de la cinta de opciones mediante el **elemento Ribbon (XML).**

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 En este tutorial se muestran las tareas siguientes:

- Agregar botones a **la pestaña Complementos.** La **pestaña Complementos es la** pestaña predeterminada que se define en el archivo XML de la cinta de opciones.

- Automatizar Microsoft Office Word mediante los botones de **la pestaña Complementos.**

> [!NOTE]
> Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-the-project"></a>Creación del proyecto
 El primer paso es crear un proyecto de complemento de VSTO de Word. Más adelante personalizará **la pestaña Complementos** de este documento.

### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto

1. Cree un **proyecto de complemento de Word** con el nombre **MyRibbonAddIn**.

     Para obtener más información, [vea Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] abre el **archivo de código ThisAddIn.cs** o **ThisAddIn.vb** y agrega el **proyecto MyRibbonAddIn** **a Explorador de soluciones**.

## <a name="create-the-vsto-add-ins-tab"></a>Creación de la pestaña Complementos de VSTO
 Para crear la **pestaña Complementos,** agregue un elemento **de cinta de opciones (XML)** al proyecto. En un paso posterior de este tutorial, agregará algunos botones a esta pestaña.

### <a name="to-create-the-add-ins-tab"></a>Para crear la pestaña Complementos

1. En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.

2. En el **cuadro de diálogo Agregar nuevo** elemento, seleccione Cinta de opciones **(XML).**

3. Cambie el nombre de la nueva cinta de opciones por **MyRibbon** y haga clic en **Agregar**.

     El **archivo MyRibbon.cs** **o MyRibbon.vb** se abre en el diseñador. Un archivo XML denominado **MyRibbon.xml** también se agrega al proyecto.

4. En **Explorador de soluciones**, haga clic con el botón derecho en **ThisAddin.cs** o **ThisAddin.vb** y, a continuación, haga clic **en Ver código**.

5. Agregue el siguiente código a la clase **ThisAddin** . Este código invalida el método `CreateRibbonExtensibilityObject` y devuelve la clase XML Ribbon a la aplicación de Office.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb" id="Snippet1":::

6. En **Explorador de soluciones**, haga clic con el botón derecho **en el proyecto MyRibbonAddIn** y, a continuación, haga clic **en Compilar**. Compruebe que el proyecto se compila sin errores.

## <a name="add-buttons-to-the-add-ins-tab"></a>Agregar botones a la pestaña Complementos
 El objetivo de este complemento de VSTO es proporcionar a los usuarios una manera de agregar texto reutilizable y una tabla específica al documento activo. Para proporcionar la interfaz de usuario, agregue dos **botones** a la pestaña Complementos modificando el archivo XML de la cinta de opciones. En un paso posterior de este tutorial, definirá métodos de devolución de llamada para los botones. Para obtener más información sobre el archivo XML de la cinta de opciones, vea [XML de cinta de opciones.](../vsto/ribbon-xml.md)

### <a name="to-add-buttons-to-the-add-ins-tab"></a>Para agregar botones a la pestaña Complementos

1. En **Explorador de soluciones**, haga clic con el botón **derecho enMyRibbon.xml** haga clic en **Abrir**.

2. Reemplace el contenido del elemento **tab** por el xml siguiente. Este XML cambia la etiqueta del grupo de controles predeterminado a **Contenido** y agrega dos nuevos botones con las etiquetas **Insertar** texto **e Insertar tabla**.

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

## <a name="automate-the-document-by-using-the-buttons"></a>Automatización del documento mediante los botones
 Debe agregar métodos de devolución de llamada para los botones Insertar texto e Insertar tabla para realizar acciones `onAction` cuando el usuario hace clic en ellos.   Para obtener más información sobre los métodos de devolución de llamada para controles de cinta de opciones, vea XML de cinta de [opciones.](../vsto/ribbon-xml.md)

### <a name="to-add-callback-methods-for-the-buttons"></a>Para agregar métodos de devolución de llamada a los botones

1. En **Explorador de soluciones**, haga clic con el botón derecho **en MyRibbon.cs** **o MyRibbon.vb** y, a continuación, haga clic **en Abrir**.

2. Agregue el código siguiente a la parte superior del **archivo MyRibbon.cs** **o MyRibbon.vb.** Este código crea un alias para el espacio de nombres <xref:Microsoft.Office.Interop.Word>.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_RibbonButtons/MyRibbon.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_RibbonButtons/MyRibbon.vb" id="Snippet1":::

3. Agrega el método siguiente a la clase `MyRibbon`: Se trata de un método de devolución de llamada para el **botón Insertar** texto que agrega una cadena al documento activo en la ubicación actual del cursor.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb" id="Snippet2":::

4. Agrega el método siguiente a la clase `MyRibbon`: Se trata de un método de devolución de llamada para el **botón Insertar** tabla que agrega una tabla al documento activo en la ubicación actual del cursor.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb" id="Snippet3":::

## <a name="testing-the-vsto-add-in"></a>Probar el complemento de VSTO
 Al ejecutar el proyecto, se abre Word y aparece **la pestaña denominada Complementos** en la cinta de opciones. Haga clic **en los botones** **Insertar** texto e Insertar tabla de la **pestaña Complementos** para probar el código.

### <a name="to-test-your-vsto-add-in"></a>Para probar el complemento de VSTO

1. Presione **F5** para ejecutar el proyecto.

2. Confirme que la **pestaña Complementos está** visible en la cinta de opciones.

3. Haga clic en la pestaña **Complementos** .

4. Confirme que el **grupo Contenido** está visible en la cinta de opciones.

5. Haga clic **en el botón Insertar** texto del **grupo** Contenido.

     Se agrega una cadena al documento en la ubicación actual del cursor.

6. Haga clic **en el botón Insertar** tabla del **grupo** Contenido.

     Se agrega una tabla al documento en la ubicación actual del cursor.

## <a name="next-steps"></a>Pasos siguientes
 Puede aprender más acerca de la personalización de la interfaz de usuario de Office en estos temas:

- Personalice la cinta de opciones de otra aplicación de Office. Para obtener más información sobre las aplicaciones que admiten la personalización de la cinta de opciones, vea Información general de la cinta de [opciones.](../vsto/ribbon-overview.md)

- Personalice la cinta de opciones de una aplicación de Office mediante el Diseñador de cinta de opciones. Para obtener más información, consulta [Ribbon Designer](../vsto/ribbon-designer.md).

- Crear un panel de acciones personalizadas. Para obtener más información, vea Información [general del panel Acciones](../vsto/actions-pane-overview.md).

- Personalizar la interfaz de usuario de Microsoft Office Outlook mediante las áreas de formulario de Outlook. Para obtener más información, [vea Tutorial: Diseño de un área de formulario de Outlook.](../vsto/walkthrough-designing-an-outlook-form-region.md)

## <a name="see-also"></a>Consulte también
- [Información general sobre la cinta de opciones](../vsto/ribbon-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Tutorial: Crear una pestaña personalizada mediante el Diseñador de cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
