---
title: Leer datos XML en un conjunto de datos | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
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
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b858a6c513c1b9e1caa4f17c1bd8af067de47365
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60114904"
---
# <a name="read-xml-data-into-a-dataset"></a>Leer datos XML en un conjunto de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ADO.NET proporciona métodos sencillos para trabajar con datos XML. En este tutorial, creará una aplicación de Windows que carga datos XML en un conjunto de datos. A continuación, se muestra el conjunto de datos en un <xref:System.Windows.Forms.DataGridView> control. Por último, se muestra un esquema XML según el contenido del archivo XML en un cuadro de texto.  
  
 En este tutorial consta de cinco pasos principales:  
  
1. Crear un nuevo proyecto  
  
2. Crear un archivo XML se lea en el conjunto de datos  
  
3. Creación de la interfaz de usuario  
  
4. Crear el conjunto de datos, leer el archivo XML y mostrarlo en un <xref:System.Windows.Forms.DataGridView> control  
  
5. Agregar código para mostrar el esquema XML basado en el archivo XML en un <xref:System.Windows.Forms.TextBox> control  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda en función de la configuración activa o la edición que está usando. Para cambiar la configuración, en el **herramientas** menú, seleccione**importar y exportar configuraciones**. Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="create-a-new-project"></a>Crear un proyecto nuevo  
 En este paso, creará un proyecto de Visual Basic o Visual C# que contiene este tutorial.  
  
#### <a name="to-create-the-new-windows-project"></a>Para crear el nuevo proyecto de Windows  
  
1. En el **archivo** menú, cree un nuevo proyecto.  
  
2. Dé un nombre al proyecto `ReadingXML`.  
  
3. Seleccione **aplicación Windows**y, a continuación, seleccione **Aceptar**. Para obtener más información, consulte [las aplicaciones cliente](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     El **ReadingXML** se crea y se agrega al proyecto **el Explorador de soluciones**.  
  
## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Generar el archivo XML se lea en el conjunto de datos  
 Dado que este tutorial se centra en la lectura de datos XML en un conjunto de datos, se proporciona el contenido de un archivo XML.  
  
#### <a name="to-create-the-xml-file-that-will-be-read-into-the-dataset"></a>Para crear el archivo XML que se leerán en el conjunto de datos  
  
1. En el **proyecto** menú, seleccione**Agregar nuevo elemento**.  
  
2. Seleccione **archivo XML**, asigne el nombre `authors.xml`y, a continuación, seleccione **agregar**.  
  
     El archivo XML se carga en el diseñador y está listo para su edición.  
  
3. Pegue el código siguiente en el editor de la declaración XML:  
  
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
  
4. En el **archivo** menú, seleccione**Guardar authors.xml**.  
  
## <a name="create-the-user-interface"></a>Crear la interfaz de usuario  
 La interfaz de usuario para esta aplicación consta de las siguientes acciones:  
  
- Un <xref:System.Windows.Forms.DataGridView> control que muestra el contenido del archivo XML como datos.  
  
- Un <xref:System.Windows.Forms.TextBox> control que muestra el esquema XML para el archivo XML.  
  
- Dos <xref:System.Windows.Forms.Button> controles.  
  
    - Lee el archivo XML en el conjunto de datos de un botón y lo muestra en el <xref:System.Windows.Forms.DataGridView> control.  
  
    - Un segundo botón extrae el esquema del conjunto de datos y, a través de un <xref:System.IO.StringWriter> lo muestra en el <xref:System.Windows.Forms.TextBox> control.  
  
#### <a name="to-add-controls-to-the-form"></a>Para agregar controles al formulario  
  
1. Abra `Form1` en la vista Diseño.  
  
2. Desde el **cuadro de herramientas**, arrastre los siguientes controles al formulario:  
  
    - Una <xref:System.Windows.Forms.DataGridView> control  
  
    - Una <xref:System.Windows.Forms.TextBox> control  
  
    - Dos <xref:System.Windows.Forms.Button> controles  
  
3. Establezca las siguientes propiedades:  
  
    |Control|Propiedad|Parámetro|  
    |-------------|--------------|-------------|  
    |`TextBox1`|**Multiline**|`true`|  
    ||**ScrollBars**|**Vertical**|  
    |`Button1`|**Name**|`ReadXmlButton`|  
    ||**Texto**|`Read XML`|  
    |`Button2`|**Name**|`ShowSchemaButton`|  
    ||**Texto**|`Show Schema`|  
  
## <a name="create-the-dataset-thatreceives-the-xml-data"></a>Crear el conjunto de datos thatreceives los datos XML  
 En este paso, creará un nuevo conjunto de datos denominado `authors`. Para obtener más información acerca de los conjuntos de datos, vea [herramientas de conjunto de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
#### <a name="to-create-a-new-dataset-that--receives-the-xml-data"></a>Para crear un nuevo conjunto de datos que recibe los datos XML  
  
1. En **el Explorador de soluciones**, seleccione el archivo de origen para **Form1**y, a continuación, seleccione el **Diseñador de vistas** situado en la **el Explorador de soluciones** barra de herramientas.  
  
2. Desde el [cuadro de herramientas, pestaña datos](../ide/reference/toolbox-data-tab.md), arrastre un **DataSet** en **Form1**.  
  
3. En el **Agregar conjunto de datos** cuadro de diálogo, seleccione **conjunto de datos sin tipo**y, a continuación, seleccione **Aceptar**.  
  
     **DataSet1** se agrega a la Bandeja de componentes.  
  
4. En el **propiedades** ventana, establezca el **nombre** y <xref:System.Data.DataSet.DataSetName%2A> propiedades para`AuthorsDataSet`.  
  
## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>Crear el controlador de eventos para leer el archivo XML en el conjunto de datos  
 El **leer XML** botón lee el archivo XML en el conjunto de datos. A continuación, Establece propiedades en el <xref:System.Windows.Forms.DataGridView> control que enlazarlo al conjunto de datos.  
  
#### <a name="to-add-code-to-the-readxmlbuttonclick-event-handler"></a>Para agregar código al controlador de eventos ReadXmlButton_Click  
  
1. En **el Explorador de soluciones**, seleccione **Form1**y, a continuación, seleccione el **Diseñador de vistas** situado en la **el Explorador de soluciones** barra de herramientas.  
  
2. Seleccione el **leer XML** botón.  
  
     El **Editor de código** se abre en el `ReadXmlButton_Click` controlador de eventos.  
  
3. Escriba el código siguiente en el `ReadXmlButton_Click` controlador de eventos:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#2)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#2)]  
  
4. En el `ReadXMLButton_Click` código de controlador de eventos, cambio el `filepath =` entrada a la ruta correcta.  
  
## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Crear el controlador de eventos para ver el esquema en el cuadro de texto  
 El **Mostrar esquema** botón crea un <xref:System.IO.StringWriter> objeto que se rellena con el esquema y se muestra en el <xref:System.Windows.Forms.TextBox>control.  
  
#### <a name="to-add-code-to-the-showschemabuttonclick-event-handler"></a>Para agregar código al controlador de eventos ShowSchemaButton_Click  
  
1. En **el Explorador de soluciones**, seleccione **Form1**y, a continuación, seleccione el **Diseñador de vistas** botón.  
  
2. Seleccione el **Mostrar esquema** botón.  
  
     El **Editor de código** se abre en el `ShowSchemaButton_Click` controlador de eventos.  
  
3. Escriba el código siguiente en el `ShowSchemaButton_Click` controlador de eventos.  
  
     [!code-csharp[VbRaddataFillingAndExecuting#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#3)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#3)]  
  
## <a name="test-the-form"></a>Comprobar el formulario  

Puede comprobar el formulario para asegurarse de que se comporta de la forma prevista.
  
1. Seleccione **F5** para ejecutar la aplicación.  
  
2. Seleccione el **leer XML** botón.  
  
     El control DataGridView muestra el contenido del archivo XML.  
  
3. Seleccione el **Mostrar esquema** botón.  
  
     El cuadro de texto muestra el esquema XML para el archivo XML.  
  
## <a name="next-steps"></a>Pasos siguientes  

En este tutorial le enseña los aspectos básicos de lectura de un archivo XML en un conjunto de datos, así como la creación de un esquema basado en el contenido del archivo XML. Estas son algunas tareas que se pueden realizar a continuación:  
  
- Editar los datos en el conjunto de datos y reescribirlos como XML. Para obtener más información, consulta <xref:System.Data.DataSet.WriteXml%2A>.  
  
- Editar los datos del conjunto de datos y escribirlos en una base de datos.
  
## <a name="see-also"></a>Vea también  
 [Tutoriales sobre datos](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
 [Preparara la aplicación para recibir datos](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Herramientas XML en Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)