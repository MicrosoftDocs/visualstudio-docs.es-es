---
title: 'Tutorial: enlazar controles de contenido a elementos XML personalizados'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- PlainTextContentControl, binding to a custom XML part
- custom XML parts, binding to content controls
- content controls [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], content controls
- DropDownListContentControl, binding items to a custom XML part
- DatePickerContentControl, binding to a custom XML part
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a80488408f680530ed3c9b4094b2997e97484ce3
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544448"
---
# <a name="walkthrough-bind-content-controls-to-custom-xml-parts"></a>Tutorial: enlazar controles de contenido a elementos XML personalizados
  Este tutorial muestra cómo enlazar controles de contenido en una personalización de nivel de documento para Word a datos XML que se almacenan en el documento.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Word permite almacenar datos XML, denominados *elementos XML personalizados*, en un documento. Puede controlar la visualización de estos datos enlazando controles de contenido a los elementos de un elemento XML personalizado. El documento de ejemplo de este tutorial muestra información de empleado que se almacena en un elemento XML personalizado. Cuando abre el documento, los controles de contenido muestran los valores de los elementos XML. Cualquier cambio que realice en el texto de los controles de contenido se guardará en el elemento XML personalizado.

 En este tutorial se muestran las tareas siguientes:

- Agregar controles de contenido al documento Word en un proyecto de nivel de documento en tiempo de diseño.

- Crear un archivo de datos XML y un esquema XML que defina los elementos que se van a enlazar a los controles de contenido.

- Asociar el esquema XML al documento en tiempo de diseño.

- Agregar el contenido del archivo XML a un elemento XML personalizado del documento en tiempo de ejecución.

- Enlazar los controles de contenido a elementos del elemento XML personalizado.

- Enlazar un <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> a un conjunto de valores que se definen en el esquema XML.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-a-new-word-document-project"></a>Crear un nuevo proyecto de documento de Word
 Crear un documento de Word que utilizará en el tutorial.

### <a name="to-create-a-new-word-document-project"></a>Para crear un nuevo proyecto de documento de Word

1. Cree un proyecto de documento de Word con el nombre **EmployeeControls**. Cree un nuevo documento para la solución. Para obtener más información, vea [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]abre el nuevo documento de Word en el diseñador y agrega el proyecto **EmployeeControls** a **Explorador de soluciones**.

## <a name="add-content-controls-to-the-document"></a>Agregar controles de contenido al documento
 Cree una tabla que contenga tres tipos diferentes de controles de contenido donde el usuario pueda ver o modificar la información sobre un empleado.

### <a name="to-add-content-controls-to-the-document"></a>Para agregar controles de contenido al documento

1. En el documento de Word que se hospeda en el [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Diseñador de, en la cinta de opciones, elija la pestaña **Insertar** .

2. En el grupo **tablas** , elija **tabla**e inserte una tabla con dos columnas y tres filas.

3. Escriba texto en la primera columna de modo que se parezca a la siguiente columna:

   ||
   |-|
   |**Nombre de empleado**|
   |**Fecha de contratación**|
   |**Título**|

4. En la segunda columna de la tabla, elija la primera fila (junto a **nombre de empleado**).

5. En la cinta de opciones, elija la pestaña **desarrollador** .

   > [!NOTE]
   > Si la pestaña **Desarrollador** no está visible, primero debe mostrarla. Para obtener más información, consulte [Cómo: Mostrar la pestaña programador en la cinta de opciones](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

6. En el grupo **controles** , elija el botón de **texto** ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") para agregar un <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> a la primera celda.

7. En la segunda columna de la tabla, elija la segunda fila (junto a **fecha de contratación**).

8. En el grupo **controles** , elija el botón **selector** de fecha ![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl") para agregar un <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> a la segunda celda.

9. En la segunda columna de la tabla, elija la tercera fila (junto a **título**).

10. En el grupo **controles** , elija el botón de **lista** desplegable ![DropDownListContentControl](../vsto/media/dropdownlist.gif "DropDownListContentControl") para agregar un <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> a la última celda.

    Esa es la interfaz de usuario completa para este proyecto. Si ejecuta ahora el proyecto, puede escribir texto en la primera fila y seleccionar una fecha en la segunda. El siguiente paso consiste en asociar los datos que desea mostrar al documento en un archivo XML.

## <a name="create-the-xml-data-file"></a>Crear el archivo de datos XML
 Por lo general, obtendrá datos XML para almacenar en un elemento XML personalizado desde un origen externo, como un archivo o una base de datos. En este tutorial creará un archivo XML que contendrá los datos del empleado, marcados mediante elementos que enlazará a los controles de contenido en el documento. Para que los datos estén disponibles en tiempo de ejecución, inserte el archivo XML como un recurso en el ensamblado de personalización.

#### <a name="to-create-the-data-file"></a>Para crear el archivo de datos

1. En el menú **Proyecto** , elija **Agregar nuevo elemento**.

     Aparecerá el cuadro de diálogo **Agregar nuevo elemento** .

2. En el panel **plantillas** , seleccione **archivo XML**.

3. Asigne un nombre al archivo **employees.xml**y, a continuación, elija el botón **Agregar** .

     El archivo de **employees.xml** se abre en el editor de código.

4. Reemplace el contenido del archivo **employees.xml** por el texto siguiente.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <employees xmlns="http://schemas.microsoft.com/vsto/samples">
      <employee>
        <name>Karina Leal</name>
        <hireDate>1999-04-01</hireDate>
        <title>Manager</title>
      </employee>
    </employees>
    ```

5. En **Explorador de soluciones**, elija el archivo de **employees.xml** .

6. En la ventana **propiedades** , seleccione la propiedad **acción de compilación** y, a continuación, cambie el valor a **recurso incrustado**.

     Este paso incrusta el archivo XML como un recurso en el ensamblado al compilar el proyecto. Esto le permite acceder al contenido del archivo XML en tiempo de ejecución.

## <a name="create-an-xml-schema"></a>Creación de un esquema XML
 Si desea enlazar un control de contenido a un único elemento en un elemento XML personalizado, no es necesario utilizar un esquema XML. Sin embargo, para enlazar el <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> a un conjunto de valores, debe crear un esquema XML que valide el archivo de datos XML que creó anteriormente. El esquema XML define los posibles valores para el elemento `title`. Enlazará el <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> a este elemento más adelante en este tutorial.

#### <a name="to-create-an-xml-schema"></a>Para crear un esquema XML

1. En el menú **Proyecto** , elija **Agregar nuevo elemento**.

     Aparecerá el cuadro de diálogo **Agregar nuevo elemento** .

2. En el panel **plantillas** , seleccione **esquema XML**.

3. Asigne al esquema el nombre **Employees. xsd** y elija el botón **Agregar** .

     Se abrirá el diseñador de esquemas.

4. En **Explorador de soluciones**, abra el menú contextual de **Employees. xsd**y, a continuación, elija **Ver código**.

5. Reemplace el contenido del archivo **Employees. xsd** por el esquema siguiente.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <xs:schema xmlns="http://schemas.microsoft.com/vsto/samples"
        targetNamespace="http://schemas.microsoft.com/vsto/samples"
        xmlns:xs="http://www.w3.org/2001/XMLSchema"
        elementFormDefault="qualified">
      <xs:element name="employees" type="EmployeesType"></xs:element>
      <xs:complexType name="EmployeesType">
        <xs:all>
          <xs:element name="employee" type="EmployeeType"/>
        </xs:all>
      </xs:complexType>
      <xs:complexType name="EmployeeType">
        <xs:sequence>
          <xs:element name="name" type="xs:string" minOccurs="1" maxOccurs="1"/>
          <xs:element name="hireDate" type="xs:date" minOccurs="1" maxOccurs="1"/>
          <xs:element name="title" type="TitleType" minOccurs="1" maxOccurs="1"/>
        </xs:sequence>
      </xs:complexType>
      <xs:simpleType name="TitleType">
        <xs:restriction base="xs:string">
          <xs:enumeration value ="Engineer"/>
          <xs:enumeration value ="Designer"/>
          <xs:enumeration value ="Manager"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:schema>
    ```

6. En el menú **archivo** , haga clic en **guardar todo** para guardar los cambios realizados en los archivos **employees.xml** y **Employees. xsd** .

## <a name="attach-the-xml-schema-to-the-document"></a>Adjuntar el esquema XML al documento
 Debe asociar el esquema XML al documento para enlazar el <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> a los valores válidos del elemento `title`.

### <a name="to-attach-the-xml-schema-to-the-document--word_15_short"></a>Para adjuntar el esquema XML al documento ( [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] )

1. Active **EmployeeControls.docx** en el diseñador.

2. En la cinta de opciones, elija la pestaña **desarrollador** y, a continuación, elija el botón **Complementos** .

3. En el cuadro de diálogo **plantillas y complementos** , elija la pestaña **esquema XML** y, a continuación, elija el botón **Agregar esquema** .

4. Vaya al esquema **Employees. xsd** que creó anteriormente, que se encuentra en el directorio del proyecto y, a continuación, elija el botón **abrir** .

5. Elija el botón **Aceptar** en el cuadro de diálogo **configuración de esquema** .

6. Elija el botón **Aceptar** para cerrar el cuadro de diálogo **plantillas y** complementos.

### <a name="to-attach-the-xml-schema-to-the-document-word-2010"></a>Para asociar el esquema XML al documento (Word 2010)

1. Active **EmployeeControls.docx** en el diseñador.

2. En la cinta de opciones, elija la pestaña **desarrollador** .

3. En el grupo **XML** , elija el botón **esquema** .

4. En el cuadro de diálogo **plantillas y complementos** , elija la pestaña **esquema XML** y, a continuación, elija el botón **Agregar esquema** .

5. Vaya al esquema **Employees. xsd** que creó anteriormente, que se encuentra en el directorio del proyecto, y elija el botón **abrir** .

6. Elija el botón **Aceptar** en el cuadro de diálogo **configuración de esquema** .

7. Elija el botón **Aceptar** para cerrar el cuadro de diálogo **plantillas y** complementos.

     Se abre el panel de tareas **estructura XML** .

8. Cierre el panel de tareas **estructura XML** .

## <a name="add-a-custom-xml-part-to-the-document"></a>Agregar un elemento XML personalizado al documento
 Antes de poder enlazar los controles de contenido a los elementos en el archivo XML, debe agregar el contenido del archivo XML a un nuevo elemento XML personalizado en el documento.

### <a name="to-add-a-custom-xml-part-to-the-document"></a>Para agregar un elemento XML personalizado al documento

1. En **Explorador de soluciones**, abra el menú contextual de **ThisDocument.CS** o **ThisDocument. VB**y, a continuación, elija **Ver código**.

2. Agregue las siguientes declaraciones a la clase `ThisDocument`. Este código declara varios objetos que utilizará para agregar un elemento XML personalizado al documento.

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#1](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#1](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#1)]

3. Agregue el siguiente método a la clase `ThisDocument`. Este método obtiene el contenido del archivo de datos XML que se incrusta como un recurso en el ensamblado y devuelve el contenido como una cadena XML.

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#3](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#3)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#3](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#3)]

4. Agregue el siguiente método a la clase `ThisDocument`. El método `AddCustomXmlPart` crea un nuevo elemento XML personalizado que contiene una cadena XML que se pasa al método.

     Para asegurarse de que el elemento XML personalizado solo se cree una vez, el método crea el elemento XML personalizado únicamente si en el documento no existe un elemento XML personalizado con un GUID coincidente. La primera vez que se llama a este método, guarda el valor de la propiedad <xref:Microsoft.Office.Core._CustomXMLPart.Id%2A> a la cadena `employeeXMLPartID`. El valor de la cadena `employeeXMLPartID` se conserva en el documento porque se declaró mediante el atributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>.

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#4](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#4)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#4](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#4)]

## <a name="bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>Enlazar los controles de contenido a elementos en el elemento XML personalizado
 Enlazar cada control de contenido a un elemento en el elemento XML personalizado mediante la propiedad **XMLMapping** de cada control de contenido.

### <a name="to-bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>Para enlazar los controles de contenido a elementos en el elemento XML personalizado

1. Agregue el siguiente método a la clase `ThisDocument`. Este método enlaza cada control de contenido a un elemento en el elemento XML personalizado y establece el formato de visualización de fecha de la <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>.

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#5](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#5)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#5](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#5)]

## <a name="run-your-code-when-the-document-is-opened"></a>Ejecutar el código cuando se abre el documento
 Cree el elemento XML personalizado y enlace los controles personalizados a los datos cuando se abre el documento.

### <a name="to-run-your-code-when-the-document-is-opened"></a>Para ejecutar el código cuando se abra el documento

1. Agregue el siguiente código al método `ThisDocument_Startup` de la clase `ThisDocument`. Este código obtiene la cadena XML del archivo **employees.xml** , agrega la cadena XML a un nuevo elemento XML personalizado del documento y enlaza los controles de contenido a los elementos del elemento XML personalizado.

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#2](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#2](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#2)]

## <a name="test-the-project"></a>Prueba del proyecto
 Cuando abre el documento, los controles de contenido muestran datos de los elementos en el elemento XML personalizado. Puede hacer clic en <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> para seleccionar uno de los tres valores válidos para el `title` elemento, que se definen en el archivo **Employees. xsd** . Si modifica los datos en cualquiera de los controles de contenido, los nuevos valores se guardan en el elemento XML personalizado en el documento.

### <a name="to-test-the-content-controls"></a>Para probar los controles de contenido

1. Presione **F5** para ejecutar el proyecto.

2. Compruebe que la tabla del documento se parece a la siguiente tabla. Cada una de las cadenas en la segunda columna se obtiene a partir de un elemento del elemento XML personalizado del documento.

    |Columna|Value|
    |-|-|
    |**Nombre de empleado**|**Karina Leal**|
    |**Fecha de contratación**|**1 de abril de 1999**|
    |**Título**|**Administrador**|

3. Elija la celda situada a la derecha de la celda **nombre de empleado** y escriba otro nombre.

4. Elija la celda situada a la derecha de la celda **fecha de contratación** y seleccione una fecha diferente en el selector de fecha.

5. Elija la celda situada a la derecha de la celda **título** y seleccione un nuevo elemento de la lista desplegable.

6. Guarde y cierre el documento.

7. En el explorador de archivos, abra la carpeta *\bin\debug* en la ubicación del proyecto.

8. Abra el menú contextual de **EmployeeControls.docx** y, a continuación, elija **cambiar nombre**.

9. Asigne al archivo el nombre **EmployeeControls.docx.zip**.

     El documento **EmployeeControls.docx** se guarda en formato Open XML. Al cambiar el nombre de este documento con la extensión de nombre de archivo *. zip* , puede examinar el contenido del documento. Para obtener más información sobre Open XML, vea el artículo técnico [Introducing The Office (2007) Open XML File Formats](/previous-versions/office/developer/office-2007/aa338205(v=office.12)).

10. Abra el archivo de **EmployeeControls.docx.zip** .

11. Abra la carpeta **customXml** .

12. Abra el menú contextual de **item2.xml** y, a continuación, elija **abrir**.

     Este archivo contiene el elemento XML personalizado que agregó al documento.

13. Compruebe que los elementos `name`, `hireDate`, y `title` contengan los nuevos valores que introdujo en los controles de contenido en el documento.

14. Cierre el archivo de **item2.xml** .

## <a name="next-steps"></a>Pasos siguientes
 Puede aprender más sobre cómo usar controles de contenido en estos temas:

- Use todos los controles de contenido disponibles para crear una plantilla. Para obtener más información, consulte [Tutorial: crear una plantilla mediante controles de contenido](../vsto/walkthrough-creating-a-template-by-using-content-controls.md).

- Modifique los datos de los elementos XML personalizados con el documento cerrado. La próxima vez que el usuario abra el documento, los controles de contenido que estén enlazados a los elementos XML mostrarán los nuevos datos.

- Utilice los controles de contenido para proteger elementos de un documento. Para obtener más información, consulte [Cómo: proteger elementos de documentos mediante controles de contenido](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).

## <a name="see-also"></a>Consulte también
- [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)
- [Controles de contenido](../vsto/content-controls.md)
- [Cómo: agregar controles de contenido a documentos de Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Cómo: proteger elementos de documentos mediante controles de contenido](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)
- [Información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md)
- [Limitaciones de programación de elementos y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)
