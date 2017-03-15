---
title: "Tutorial: Leer datos XML e introducirlos en un conjunto de datos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "datos [Visual Studio], leer de archivos XML"
  - "acceso a datos [Visual Studio], datos XML"
  - "conjuntos de datos [Visual Basic], leer datos XML"
  - "leer datos, XML (archivos)"
  - "leer archivos, XML"
  - "leer XML"
  - "XML [Visual Studio], leer"
  - "XML (documentos), leer"
ms.assetid: fae72958-0893-47d6-b3dd-9d42418418e4
caps.latest.revision: 18
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tutorial: Leer datos XML e introducirlos en un conjunto de datos
ADO.NET proporciona métodos sencillos para trabajar con datos XML.  En este tutorial, se creará una aplicación para Windows que cargará datos XML en un conjunto de datos.  Después, el conjunto de datos se mostrará en un control <xref:System.Windows.Forms.DataGridView>.  Por último, se mostrará en un cuadro de texto un esquema XML basado en el contenido del archivo XML.  
  
 Este tutorial consta de cinco pasos principales:  
  
1.  Crear un proyecto nuevo.  
  
2.  Crear un archivo XML que se leerá en el conjunto de datos.  
  
3.  Crear la interfaz de usuario.  
  
4.  Crear el conjunto de datos, leer el archivo XML y mostrarlo en un control <xref:System.Windows.Forms.DataGridView>.  
  
5.  Agregar código para mostrar en un control <xref:System.Windows.Forms.TextBox> el esquema XML basado en el archivo XML.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar la configuración, elija **Importar y exportar configuraciones** en el menú **Herramientas**.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Crear un nuevo proyecto  
 En este paso, creará un proyecto de Visual Basic o Visual C\# que incluirá este tutorial.  
  
#### Para crear el nuevo proyecto de Windows  
  
1.  En el menú **Archivo**, cree un nuevo proyecto.  
  
2.  Asigne al proyecto el nombre `ReadingXML`.  
  
3.  Seleccione **Aplicación para Windows** y haga clic en **Aceptar**.  Para obtener más información, vea [Aplicaciones cliente](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Se crea el proyecto **ReadingXML** y se agrega al Explorador de soluciones.  
  
## Generar el archivo XML que será leído en el conjunto de datos  
 Debido a que este tutorial se centra en la lectura de datos XML en un conjunto de datos, se proporciona el contenido de un archivo XML.  
  
#### Para crear el archivo XML que será leído en el conjunto de datos  
  
1.  En el menú **Proyecto**, elija **Agregar nuevo elemento**.  
  
2.  Seleccione **Archivo XML**, asigne al archivo el nombre `authors.xml` y haga clic en **Agregar**.  
  
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
  
4.  En el menú **Archivo**, seleccione **Guardar authors.xml**.  
  
## Crear la interfaz de usuario  
 La interfaz de usuario para esta aplicación constará de los siguientes elementos:  
  
-   Un control <xref:System.Windows.Forms.DataGridView> que mostrará el contenido del archivo XML como datos.  
  
-   Un control <xref:System.Windows.Forms.TextBox> que mostrará el esquema XML del archivo XML.  
  
-   Dos controles <xref:System.Windows.Forms.Button>.  
  
    -   Un botón lee el archivo XML en el conjunto de datos y lo muestra en el control <xref:System.Windows.Forms.DataGridView>.  
  
    -   El segundo botón extrae el esquema del conjunto de datos y, a través de un <xref:System.IO.StringWriter>, lo muestra en el control <xref:System.Windows.Forms.TextBox>.  
  
#### Para agregar controles al formulario  
  
1.  Abra `Form1` en la vista de diseño.  
  
2.  En el **Cuadro de herramientas**, arrastre los controles siguientes hasta el formulario:  
  
    -   Un control <xref:System.Windows.Forms.DataGridView>  
  
    -   Un control <xref:System.Windows.Forms.TextBox>  
  
    -   Dos controles <xref:System.Windows.Forms.Button>  
  
3.  Establezca las siguientes propiedades:  
  
    |Control|Propiedad.|Configuración|  
    |-------------|----------------|-------------------|  
    |`TextBox1`|**Multiline**|`true`|  
    ||**ScrollBars**|**Vertical**|  
    |`Button1`|**Name**|`ReadXmlButton`|  
    ||**Text**|`Read XML`|  
    |`Button2`|**Name**|`ShowSchemaButton`|  
    ||**Text**|`Show Schema`|  
  
## Crear el conjunto de datos que recibirá los datos XML  
 En este procedimiento siguiente, se crea un nuevo conjunto de datos denominado `authors`.  Para obtener más información sobre conjuntos de datos, vea [Trabajar con los conjuntos de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
#### Para crear un nuevo conjunto de datos que recibirá los datos XML  
  
1.  Con el archivo de código fuente para **Form1** seleccionado en el **Explorador de soluciones**, haga clic en el botón **Diseñador de vistas** en la barra de herramientas **Explorador de soluciones**.  
  
2.  Desde [Cuadro de herramientas, Datos \(Pestaña\)](../ide/reference/toolbox-data-tab.md), arrastre un **Conjunto de datos** hasta **Form1**.  
  
3.  **Conjunto de datos sin tipo** seleccione en el cuadro de diálogo de **Agregar conjunto de datos** , y haga clic en **Aceptar**.  
  
     **DataSet1** se agrega a la bandeja de componentes.  
  
4.  En la ventana **Propiedades**, establezca las propiedades **Nombre** y <xref:System.Data.DataSet.DataSetName%2A> en `AuthorsDataSet`.  
  
## Crear el controlador de eventos para leer los datos XML en el conjunto de datos  
 El botón **Leer XML** lee el archivo XML en el conjunto de datos y establece propiedades en el control <xref:System.Windows.Forms.DataGridView> que lo enlaza al conjunto de datos.  
  
#### Para agregar código al controlador de eventos ReadXmlButton\_Click  
  
1.  En el **Explorador de soluciones**, seleccione **Form1** y haga clic en el botón **Diseñador de vistas** del **Explorador de soluciones**.  
  
2.  Haga doble clic en el botón **Leer XML**.  
  
     Se abrirá el **Editor de código** en el controlador de eventos `ReadXmlButton_Click`.  
  
3.  Escriba el código siguiente en el controlador de eventos `ReadXmlButton_Click`:  
  
     [!code-cs[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_1.vb)]  
  
4.  En el código del controlador de eventos `ReadXMLButton_Click`, cambie la entrada `filepath =` a la ruta de acceso correcta.  
  
## Crear el controlador de eventos para mostrar el esquema en el control TextBox  
 El botón **Mostrar esquema** crea un objeto <xref:System.IO.StringWriter> que se llena con el esquema y se muestra en el control <xref:System.Windows.Forms.TextBox>.  
  
#### Para agregar código al controlador de eventos ShowSchemaButton\_Click  
  
1.  En el **Explorador de soluciones**, seleccione **Form1** y haga clic en el botón **Diseñador de vistas**.  
  
2.  Haga doble clic en el botón **Mostrar esquema**.  
  
     Se abrirá el **Editor de código** en el controlador de eventos `ShowSchemaButton_Click`.  
  
3.  Escriba el código siguiente en el controlador de eventos `ShowSchemaButton_Click`.  
  
     [!code-cs[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_2.vb)]  
  
## Pruebas  
 Puede comprobar el formulario para asegurarse de que se comporta de la forma prevista.  
  
#### Para comprobar el formulario  
  
1.  Presione F5 para ejecutar la aplicación.  
  
2.  Haga clic en el botón **Leer XML**.  
  
     El control DataGridView muestra el contenido del archivo XML.  
  
3.  Haga clic en el botón **Mostrar esquema**.  
  
     El cuadro de texto muestra el esquema XML del archivo XML.  
  
## Pasos siguientes  
 Este tutorial muestra los pasos básicos para leer un archivo XML en un conjunto de datos, así como crear un esquema basado en el contenido del archivo XML.  Éstas son algunas de las tareas que pueden venir a continuación:  
  
-   Editar los datos del conjunto de datos y volver a escribirlos como XML.  Para obtener más información, vea <xref:System.Data.DataSet.WriteXml%2A>.  
  
-   Editar los datos del conjunto de datos y escribirlos en una base de datos.  Para obtener más información, vea [Guardar datos](../data-tools/saving-data.md).  
  
## Vea también  
 [Tutoriales sobre datos](../Topic/Data%20Walkthroughs.md)   
 [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Herramientas XML en Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)