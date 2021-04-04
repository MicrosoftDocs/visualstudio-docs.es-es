---
title: Leer datos XML en un conjunto de datos
description: Leer datos XML en un conjunto de datos. En este tutorial, creará una aplicación de Windows que carga datos XML en un conjunto de datos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: b3a238bf325819b340b983618b5aac8f723184f4
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216194"
---
# <a name="read-xml-data-into-a-dataset"></a>Leer datos XML en un conjunto de datos

ADO.NET proporciona métodos sencillos para trabajar con datos XML. En este tutorial, creará una aplicación de Windows que carga datos XML en un conjunto de datos. Después, el conjunto de DataSet se muestra en un <xref:System.Windows.Forms.DataGridView> control. Por último, en un cuadro de texto se muestra un esquema XML basado en el contenido del archivo XML.

## <a name="create-a-new-project"></a>Creación de un nuevo proyecto

Cree un nuevo proyecto de **aplicación de Windows Forms** para C# o Visual Basic. Asigne al proyecto el nombre **ReadingXML**.

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Generar el archivo XML que se leerá en el conjunto de archivos

Dado que este tutorial se centra en la lectura de datos XML en un conjunto de datos, se proporciona el contenido de un archivo XML.

1. En el menú **Proyecto**, seleccione **Agregar nuevo elemento**.

2. Seleccione **archivo XML**, asigne un nombre al archivo **authors.xml** y, a continuación, seleccione **Agregar**.

   El archivo XML se carga en el diseñador y está listo para su edición.

3. Pegue los siguientes datos XML en el editor debajo de la declaración XML:

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

4. En el menú **archivo** , seleccione **Guardar authors.xml**.

## <a name="create-the-user-interface"></a>Creación de la interfaz del usuario

La interfaz de usuario de esta aplicación se compone de lo siguiente:

- <xref:System.Windows.Forms.DataGridView>Control que muestra el contenido del archivo XML como datos.

- Un <xref:System.Windows.Forms.TextBox> control que muestra el esquema XML para el archivo XML.

- Dos <xref:System.Windows.Forms.Button> controles.

  - Un botón lee el archivo XML en el conjunto de archivos y lo muestra en el <xref:System.Windows.Forms.DataGridView> control.

  - Un segundo botón extrae el esquema del conjunto de DataSet y, a través de un, <xref:System.IO.StringWriter> lo muestra en el <xref:System.Windows.Forms.TextBox> control.

### <a name="to-add-controls-to-the-form"></a>Para agregar controles al formulario

1. Abra `Form1` en la vista Diseño.

2. En el **cuadro de herramientas**, arrastre los siguientes controles al formulario:

    - Un <xref:System.Windows.Forms.DataGridView> control

    - Un <xref:System.Windows.Forms.TextBox> control

    - Dos <xref:System.Windows.Forms.Button> controles

3. Establezca las siguientes propiedades:

    |Control|Propiedad|Parámetro|
    |-------------|--------------|-------------|
    |`TextBox1`|**Multiline**|`true`|
    ||**ScrollBars**|**Vertical**|
    |`Button1`|**Nombre**|`ReadXmlButton`|
    ||**Texto**|`Read XML`|
    |`Button2`|**Nombre**|`ShowSchemaButton`|
    ||**Texto**|`Show Schema`|

## <a name="create-the-dataset-that-receives-the-xml-data"></a>Crear el conjunto de datos que recibe los datos XML

En este paso, creará un nuevo conjunto de nuevos denominado `authors` . Para obtener más información acerca de los conjuntos de datos, vea [herramientas de conjunto de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

1. En **Explorador de soluciones**, seleccione el archivo de origen de **Form1** y, a continuación, seleccione el botón **Diseñador de vistas** en la barra de herramientas **Explorador de soluciones** .

2. En el [cuadro de herramientas, pestaña datos](../ide/reference/toolbox-data-tab.md), arrastre un **conjunto** de datos hasta **Form1**.

3. En el cuadro de diálogo **Agregar conjunto** de propiedades, seleccione **conjunto de tipos sin tipo** y, a continuación, haga clic en **Aceptar**.

     **DataSet1** se agrega a la bandeja de componentes.

4. En la ventana **propiedades** , establezca el **nombre** y <xref:System.Data.DataSet.DataSetName%2A> las propiedades de `AuthorsDataSet` .

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>Crear el controlador de eventos para leer el archivo XML en el conjunto de archivos

El botón **leer XML** lee el archivo XML en el conjunto de archivos. A continuación, establece las propiedades del <xref:System.Windows.Forms.DataGridView> control que lo enlazan al conjunto de DataSet.

1. En **Explorador de soluciones**, seleccione **Form1** y, a continuación, seleccione el botón **Diseñador de vistas** en la barra de herramientas **Explorador de soluciones** .

2. Seleccione el botón **leer XML** .

     El **Editor de código** se abre en el `ReadXmlButton_Click` controlador de eventos.

3. Escriba el código siguiente en el `ReadXmlButton_Click` controlador de eventos:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb" id="Snippet2":::

4. En el `ReadXMLButton_Click` código del controlador de eventos, cambie la `filepath =` entrada a la ruta de acceso correcta.

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Crear el controlador de eventos para mostrar el esquema en el cuadro de texto

El botón **Mostrar esquema** crea un <xref:System.IO.StringWriter> objeto que se rellena con el esquema y se muestra en el <xref:System.Windows.Forms.TextBox> control.

1. En **Explorador de soluciones**, seleccione **Form1** y, a continuación, seleccione el botón **Diseñador de vistas** .

2. Seleccione el botón **Mostrar esquema** .

     El **Editor de código** se abre en el `ShowSchemaButton_Click` controlador de eventos.

3. Pegue el código siguiente en el controlador de eventos `ShowSchemaButton_Click`.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb" id="Snippet3":::

## <a name="test-the-form"></a>Prueba del formulario

Puede comprobar el formulario para asegurarse de que se comporta de la forma prevista.

1. Seleccione **F5** para ejecutar la aplicación.

2. Seleccione el botón **leer XML** .

     DataGridView muestra el contenido del archivo XML.

3. Seleccione el botón **Mostrar esquema** .

     En el cuadro de texto se muestra el esquema XML del archivo XML.

## <a name="next-steps"></a>Pasos siguientes

Este tutorial le enseña los aspectos básicos de la lectura de un archivo XML en un conjunto de datos, así como la creación de un esquema basado en el contenido del archivo XML. Estas son algunas de las tareas que puede realizar a continuación:

- Edite los datos del conjunto de datos y vuelva a escribirlos como XML. Para más información, consulte <xref:System.Data.DataSet.WriteXml%2A>.

- Edite los datos del conjunto de datos y escríbalos en una base de datos.

## <a name="see-also"></a>Consulte también

- [Acceso a datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Herramientas XML en Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)
