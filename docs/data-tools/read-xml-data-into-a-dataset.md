---
title: Leer datos XML en un conjunto de datos
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- reading XML
- data access [Visual Studio], XML data
- reading files, XML
- data [Visual Studio], reading from XML files
- reading data, XML files
- XML [Visual Studio], reading
- XML documents, reading
- datasets [Visual Basic], reading XML data
ms.assetid: fae72958-0893-47d6-b3dd-9d42418418e4
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d54811f2fe46733d256a473c5fcb1c523a15a71e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="read-xml-data-into-a-dataset"></a>Leer datos XML en un conjunto de datos
ADO.NET proporciona métodos sencillos para trabajar con datos XML. En este tutorial, creará una aplicación para Windows que carga datos XML en un conjunto de datos. A continuación, se muestra el conjunto de datos en un <xref:System.Windows.Forms.DataGridView> control. Por último, se muestra un esquema XML basado en el contenido del archivo XML en un cuadro de texto.

 Este tutorial consta de cinco pasos principales:

1.  Crear un nuevo proyecto

2.  Crear un archivo XML que será leído en el conjunto de datos

3.  Creación de la interfaz de usuario

4.  Crear el conjunto de datos, leer el archivo XML y mostrarlo en un <xref:System.Windows.Forms.DataGridView> control

5.  Agregar código para mostrar el esquema XML basado en el archivo XML en un <xref:System.Windows.Forms.TextBox> control

> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, dependiendo de la edición o la configuración activa que esté utilizando. Para cambiar la configuración, en la **herramientas** menú, seleccione **importar y exportar configuraciones**. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-new-project"></a>Crear un proyecto nuevo
 En este paso, creará un proyecto de Visual Basic o Visual C# que contiene este tutorial.

#### <a name="to-create-the-new-windows-project"></a>Para crear el nuevo proyecto de Windows

1. En Visual Studio, en el **archivo** menú, seleccione **New**, **proyecto...** .

2. Expanda **Visual C#** o **Visual Basic** en el panel izquierdo, seleccione **escritorio clásico de Windows**.

3. En el panel central, seleccione la **aplicación de Windows Forms** tipo de proyecto.

4. Denomine el proyecto **ReadingXML**y, a continuación, elija **Aceptar**.

     El **ReadingXML** se crea y se agrega al proyecto **el Explorador de soluciones**.

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Generar el archivo XML que será leído en el conjunto de datos
 Dado que este tutorial se centra en la lectura de datos XML en un conjunto de datos, se proporciona el contenido de un archivo XML.

#### <a name="to-create-the-xml-file-that-will-be-read-into-the-dataset"></a>Para crear el archivo XML que se leerán en el conjunto de datos

1.  En el **proyecto** menú, seleccione **Agregar nuevo elemento**.

2.  Seleccione **archivo XML**, un nombre al archivo `authors.xml`y, a continuación, seleccione **agregar**.

     El archivo XML se carga en el diseñador y está listo para su edición.

3.  Pegue el código siguiente en el editor, debajo de la declaración XML:

    ```xml
    <Authors_Table>
      <authors>
        <au_id>172-32-1176</au_id>
        <au_lname>White</au_lname>
        <au_fname>Johnson</au_fname>
        <phone>408 496-7223</phone>
        <address>10932 Bigge Rd.</address>
        <city>Menlo Park</city>
        <state>CA</state>
        <zip>94025</zip>
        <contract>true</contract>
      </authors>
      <authors>
        <au_id>213-46-8915</au_id>
        <au_lname>Green</au_lname>
        <au_fname>Margie</au_fname>
        <phone>415 986-7020</phone>
        <address>309 63rd St. #411</address>
        <city>Oakland</city>
        <state>CA</state>
        <zip>94618</zip>
        <contract>true</contract>
      </authors>
      <authors>
        <au_id>238-95-7766</au_id>
        <au_lname>Carson</au_lname>
        <au_fname>Cheryl</au_fname>
        <phone>415 548-7723</phone>
        <address>589 Darwin Ln.</address>
        <city>Berkeley</city>
        <state>CA</state>
        <zip>94705</zip>
        <contract>true</contract>
      </authors>
      <authors>
        <au_id>267-41-2394</au_id>
        <au_lname>Hunter</au_lname>
        <au_fname>Anne</au_fname>
        <phone>408 286-2428</phone>
        <address>22 Cleveland Av. #14</address>
        <city>San Jose</city>
        <state>CA</state>
        <zip>95128</zip>
        <contract>true</contract>
      </authors>
      <authors>
        <au_id>274-80-9391</au_id>
        <au_lname>Straight</au_lname>
        <au_fname>Dean</au_fname>
        <phone>415 834-2919</phone>
        <address>5420 College Av.</address>
        <city>Oakland</city>
        <state>CA</state>
        <zip>94609</zip>
        <contract>true</contract>
      </authors>
    </Authors_Table>
    ```

4.  En el **archivo** menú, seleccione **Guardar authors.xml**.

## <a name="create-the-user-interface"></a>Crear la interfaz de usuario
 La interfaz de usuario para esta aplicación consta de las siguientes acciones:

-   Un <xref:System.Windows.Forms.DataGridView> control que muestra el contenido del archivo XML como datos.

-   Un <xref:System.Windows.Forms.TextBox> control que muestra el esquema XML para el archivo XML.

-   Dos <xref:System.Windows.Forms.Button> controles.

    -   Un botón lee el archivo XML en el conjunto de datos y lo muestra en el <xref:System.Windows.Forms.DataGridView> control.

    -   Un segundo botón extrae el esquema del conjunto de datos y a través de un <xref:System.IO.StringWriter> lo muestra en el <xref:System.Windows.Forms.TextBox> control.

#### <a name="to-add-controls-to-the-form"></a>Para agregar controles al formulario

1.  Abra `Form1` en la vista Diseño.

2.  Desde el **cuadro de herramientas**, arrastre los siguientes controles al formulario:

    -   Una <xref:System.Windows.Forms.DataGridView> control

    -   Una <xref:System.Windows.Forms.TextBox> control

    -   Dos <xref:System.Windows.Forms.Button> controles

3.  Establezca las siguientes propiedades:

    |Control|Property|Parámetro|
    |-------------|--------------|-------------|
    |`TextBox1`|**Multiline**|`true`|
    ||**Barras de desplazamiento**|**Vertical**|
    |`Button1`|**Name**|`ReadXmlButton`|
    ||**Texto**|`Read XML`|
    |`Button2`|**Name**|`ShowSchemaButton`|
    ||**Texto**|`Show Schema`|

## <a name="create-the-dataset-that-receives-the-xml-data"></a>Crear el conjunto de datos que recibe los datos XML
 En este paso, creará un nuevo conjunto de datos denominado `authors`. Para obtener más información acerca de los conjuntos de datos, vea [herramientas de conjunto de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

#### <a name="to-create-a-new-dataset-that-receives-the-xml-data"></a>Para crear un nuevo conjunto de datos que recibe los datos XML

1.  En **el Explorador de soluciones**, seleccione el archivo de origen para **Form1**y, a continuación, seleccione la **Diseñador de vistas** situado en la **el Explorador de soluciones** barra de herramientas.

2.  Desde el [cuadro de herramientas, pestaña datos](../ide/reference/toolbox-data-tab.md), arrastre un **conjunto de datos** en **Form1**.

3.  En el **Agregar conjunto de datos** cuadro de diálogo, seleccione **conjunto de datos sin tipo**y, a continuación, seleccione **Aceptar**.

     **DataSet1** se agrega a la Bandeja de componentes.

4.  En el **propiedades** ventana, establezca el **nombre** y <xref:System.Data.DataSet.DataSetName%2A> propiedades de`AuthorsDataSet`.

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>Crear el controlador de eventos para leer el archivo XML en el conjunto de datos
 El **leer XML** botón lee el archivo XML en el conjunto de datos. A continuación, Establece propiedades en el <xref:System.Windows.Forms.DataGridView> control que se enlazan al conjunto de datos.

#### <a name="to-add-code-to-the-readxmlbuttonclick-event-handler"></a>Para agregar código al controlador de eventos ReadXmlButton_Click

1.  En **el Explorador de soluciones**, seleccione **Form1**y, a continuación, seleccione la **Diseñador de vistas** situado en la **el Explorador de soluciones** barra de herramientas.

2.  Seleccione el **leer XML** botón.

     El **Editor de código** se abre en el `ReadXmlButton_Click` controlador de eventos.

3.  Escriba el código siguiente en el `ReadXmlButton_Click` controlador de eventos:

     [!code-csharp[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_1.vb)]

4.  En el `ReadXMLButton_Click` código del controlador de eventos, cambiar el `filepath =` entrada a la ruta de acceso correcta.

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Crear el controlador de eventos para ver el esquema en el cuadro de texto
 El **Mostrar esquema** botón crea un <xref:System.IO.StringWriter> objeto que se rellena con el esquema y se muestra en el <xref:System.Windows.Forms.TextBox>control.

#### <a name="to-add-code-to-the-showschemabuttonclick-event-handler"></a>Para agregar código al controlador de eventos ShowSchemaButton_Click

1.  En **el Explorador de soluciones**, seleccione **Form1**y, a continuación, seleccione la **Diseñador de vistas** botón.

2.  Seleccione el **Mostrar esquema** botón.

     El **Editor de código** se abre en el `ShowSchemaButton_Click` controlador de eventos.

3.  Escriba el código siguiente en el `ShowSchemaButton_Click` controlador de eventos.

     [!code-csharp[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_2.vb)]

## <a name="test-the-form"></a>Comprobar el formulario
 Puede comprobar el formulario para asegurarse de que se comporta de la forma prevista.

#### <a name="to-test-the-form"></a>Para comprobar el formulario

1.  Seleccione **F5** para ejecutar la aplicación.

2.  Seleccione el **leer XML** botón.

     El control DataGridView muestra el contenido del archivo XML.

3.  Seleccione el **Mostrar esquema** botón.

     El cuadro de texto muestra el esquema XML para el archivo XML.

## <a name="next-steps"></a>Pasos siguientes
 Este tutorial le enseña los fundamentos de leer un archivo XML en un conjunto de datos, así como crear un esquema basado en el contenido del archivo XML. Hay algunas tareas que puede realizar a continuación:

-   Editar los datos en el conjunto de datos y escribirlos de como XML. Para obtener más información, consulta <xref:System.Data.DataSet.WriteXml%2A>.

-   Editar los datos del conjunto de datos y escribirlos en una base de datos. Para obtener más información, consulte [guardar datos](../data-tools/saving-data.md).

## <a name="see-also"></a>Vea también

- [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Herramientas XML en Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)