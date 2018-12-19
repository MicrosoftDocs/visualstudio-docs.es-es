---
title: 'Tutorial: Enlazar controles de contenido a elementos XML personalizados'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 05d7c3cc2c391eee6ceeba492cd083efd3c00015
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49916756"
---
# <a name="walkthrough-bind-content-controls-to-custom-xml-parts"></a>Tutorial: Enlazar controles de contenido a elementos XML personalizados
  Este tutorial muestra cómo enlazar controles de contenido en una personalización de nivel de documento para Word a datos XML que se almacenan en el documento.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Word le permite almacenar datos XML, denominados *elementos XML personalizados*, en un documento. Puede controlar la visualización de estos datos enlazando controles de contenido a los elementos de un elemento XML personalizado. El documento de ejemplo de este tutorial muestra información de empleado que se almacena en un elemento XML personalizado. Cuando abre el documento, los controles de contenido muestran los valores de los elementos XML. Cualquier cambio que realice en el texto de los controles de contenido se guardará en el elemento XML personalizado.  
  
 En este tutorial se muestran las tareas siguientes:  
  
- Agregar controles de contenido al documento Word en un proyecto de nivel de documento en tiempo de diseño.  
  
- Crear un archivo de datos XML y un esquema XML que defina los elementos que se van a enlazar a los controles de contenido.  
  
- Asociar el esquema XML al documento en tiempo de diseño.  
  
- Agregar el contenido del archivo XML a un elemento XML personalizado en el documento en tiempo de ejecución.  
  
- Enlazar los controles de contenido a elementos del elemento XML personalizado.  
  
- Enlazar un <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> a un conjunto de valores que se definen en el esquema XML.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## <a name="create-a-new-word-document-project"></a>Crear un nuevo proyecto de documento de Word  
 Crear un documento de Word que utilizará en el tutorial.  
  
### <a name="to-create-a-new-word-document-project"></a>Para crear un nuevo proyecto de documento de Word  
  
1.  Cree un proyecto de documento de Word con el nombre **EmployeeControls**. Cree un nuevo documento para la solución. Para obtener más información, consulte [Cómo: proyectos de creación de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Abre el nuevo documento de Word en el diseñador y agrega el **EmployeeControls** proyecto a **el Explorador de soluciones**.  
  
## <a name="add-content-controls-to-the-document"></a>Agregar controles de contenido al documento  
 Cree una tabla que contenga tres tipos diferentes de controles de contenido donde el usuario pueda ver o modificar la información sobre un empleado.  
  
### <a name="to-add-content-controls-to-the-document"></a>Para agregar controles de contenido al documento  
  
1. En el documento de Word que se hospeda en el [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] diseñador, en la cinta de opciones, elija la **insertar** ficha.  
  
2. En el **tablas** grupo, elija **tabla**e inserte una tabla con 2 columnas y 3 filas.  
  
3. Escriba texto en la primera columna de modo que se parezca a la siguiente columna:  
  
   ||  
   |-|  
   |**Nombre de empleado**|  
   |**Fecha de contratación**|  
   |**Título**|  
  
4. En la segunda columna de la tabla, elija la primera fila (junto a **nombre empleado**).  
  
5. En la cinta de opciones, elija la **Developer** ficha.  
  
   > [!NOTE]  
   >  Si la pestaña **Desarrollador** no está visible, primero debe mostrarla. Para obtener más información, consulte [Cómo: mostrar la pestaña Programador en la cinta de opciones](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
6. En el **controles** grupo, elija la **texto** botón ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") para agregar un <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>a la primera celda.  
  
7. En la segunda columna de la tabla, elija la segunda fila (junto a **fecha de contratación**).  
  
8. En el **controles** grupo, elija la **selector de fecha** botón ![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl") para agregar un <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> a la segunda celda.  
  
9. En la segunda columna de la tabla, elija la tercera fila (junto a **título**).  
  
10. En el **controles** grupo, elija la **lista desplegable** botón ![DropDownListContentControl](../vsto/media/dropdownlist.gif "DropDownListContentControl") para agregar un <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> a la última celda.  
  
    Esa es la interfaz de usuario completa para este proyecto. Si ejecuta ahora el proyecto, puede escribir texto en la primera fila y seleccionar una fecha en la segunda. El siguiente paso consiste en asociar los datos que desea mostrar al documento en un archivo XML.  
  
## <a name="create-the-xml-data-file"></a>Crear el archivo de datos XML  
 Por lo general, obtendrá datos XML para almacenar en un elemento XML personalizado desde un origen externo, como un archivo o una base de datos. En este tutorial creará un archivo XML que contendrá los datos del empleado, marcados mediante elementos que enlazará a los controles de contenido en el documento. Para que los datos estén disponibles en tiempo de ejecución, incruste el archivo XML como un recurso en el ensamblado de personalización.  
  
#### <a name="to-create-the-data-file"></a>Para crear el archivo de datos  
  
1.  En el menú **Proyecto** , elija **Agregar nuevo elemento**.  
  
     Aparecerá el cuadro de diálogo **Agregar nuevo elemento**.  
  
2.  En el **plantillas** panel, seleccione **archivo XML**.  
  
3.  Nombre del archivo **employees.xml**y, a continuación, elija el **agregar** botón.  
  
     El **employees.xml** archivo se abre en el Editor de código.  
  
4.  Reemplace el contenido de la **employees.xml** archivo con el siguiente texto.  
  
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
  
5.  En **el Explorador de soluciones**, elija el **employees.xml** archivo.  
  
6.  En el **propiedades** ventana, seleccione el **acción de compilación** propiedad y, a continuación, cambie el valor a **recurso incrustado**.  
  
     Este paso incrusta el archivo XML como un recurso en el ensamblado al compilar el proyecto. Esto le permite tener acceso al contenido del archivo XML en tiempo de ejecución.  
  
## <a name="create-an-xml-schema"></a>Crear un esquema XML  
 Si desea enlazar un control de contenido a un único elemento en un elemento XML personalizado, no es necesario utilizar un esquema XML. Sin embargo, para enlazar el <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> a un conjunto de valores, debe crear un esquema XML que valide el archivo de datos XML que creó anteriormente. El esquema XML define los posibles valores para el elemento `title`. Enlazará el <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> a este elemento más adelante en este tutorial.  
  
#### <a name="to-create-an-xml-schema"></a>Para crear un esquema XML  
  
1.  En el menú **Proyecto** , elija **Agregar nuevo elemento**.  
  
     Aparecerá el cuadro de diálogo **Agregar nuevo elemento**.  
  
2.  En el **plantillas** panel, seleccione **esquema XML**.  
  
3.  Nombre del esquema **employees.xsd** y elija el **agregar** botón.  
  
     Se abrirá el diseñador de esquemas.  
  
4.  En **el Explorador de soluciones**, abra el menú contextual para **employees.xsd**y, a continuación, elija **ver código**.  
  
5.  Reemplace el contenido de la **employees.xsd** archivo con el siguiente esquema.  
  
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
  
6.  En el **archivo** menú, haga clic en **guardar todo** para guardar los cambios realizados en el **employees.xml** y **employees.xsd** archivos.  
  
## <a name="attach-the-xml-schema-to-the-document"></a>Asociar el esquema XML al documento  
 Debe asociar el esquema XML al documento para enlazar el <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> a los valores válidos del elemento `title`.  
  
### <a name="to-attach-the-xml-schema-to-the-document--includeword15shortvstoincludesword-15-short-mdmd"></a>Para asociar el esquema XML al documento ( [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)])  
  
1.  Activar **EmployeeControls.docx** en el diseñador.  
  
2.  En la cinta de opciones, elija la **Developer** pestaña y, a continuación, elija el **Add-Ins** botón.  
  
3.  En el **plantillas y complementos** diálogo cuadro, elija el **esquema XML** pestaña y, a continuación, elija el **Agregar esquema** botón.  
  
4.  Vaya a la **employees.xsd** esquema que creó anteriormente, que se encuentra en el directorio del proyecto y, a continuación, elija el **abierto** botón.  
  
5.  Elija la **Aceptar** situado en la **configuración del esquema** cuadro de diálogo.  
  
6.  Elija la **Aceptar** botón para cerrar el **plantillas y complementos** cuadro de diálogo.  
  
### <a name="to-attach-the-xml-schema-to-the-document-word-2010"></a>Para asociar el esquema XML al documento (Word 2010)  
  
1.  Activar **EmployeeControls.docx** en el diseñador.  
  
2.  En la cinta de opciones, elija la **Developer** ficha.  
  
3.  En el **XML** grupo, elija la **esquema** botón.  
  
4.  En el **plantillas y complementos** diálogo cuadro, elija el **esquema XML** pestaña y, a continuación, elija el **Agregar esquema** botón.  
  
5.  Vaya a la **employees.xsd** esquema que creó anteriormente, que se encuentra en el directorio del proyecto y elija el **abierto** botón.  
  
6.  Elija la **Aceptar** situado en la **configuración del esquema** cuadro de diálogo.  
  
7.  Elija la **Aceptar** botón para cerrar el **plantillas y complementos** cuadro de diálogo.  
  
     El **estructura XML** abre el panel de tareas.  
  
8.  Cerrar la **estructura XML** panel de tareas.  
  
## <a name="add-a-custom-xml-part-to-the-document"></a>Agregar un elemento XML personalizado al documento  
 Antes de poder enlazar los controles de contenido a los elementos en el archivo XML, debe agregar el contenido del archivo XML a un nuevo elemento XML personalizado en el documento.  
  
### <a name="to-add-a-custom-xml-part-to-the-document"></a>Para agregar un elemento XML personalizado al documento  
  
1.  En **el Explorador de soluciones**, abra el menú contextual para **ThisDocument.cs** o **ThisDocument.vb**y, a continuación, elija **ver código**.  
  
2.  Agregue las siguientes declaraciones a la clase `ThisDocument`. Este código declara varios objetos que utilizará para agregar un elemento XML personalizado al documento.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#1](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#1](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#1)]  
  
3.  Agregue el método siguiente a la clase `ThisDocument`. Este método obtiene el contenido del archivo de datos XML que se incrusta como un recurso en el ensamblado y devuelve el contenido como una cadena XML.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#3](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#3)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#3](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#3)]  
  
4.  Agregue el método siguiente a la clase `ThisDocument`. El método `AddCustomXmlPart` crea un nuevo elemento XML personalizado que contiene una cadena XML que se pasa al método.  
  
     Para asegurarse de que el elemento XML personalizado solo se cree una vez, el método crea el elemento XML personalizado únicamente si en el documento no existe un elemento XML personalizado con un GUID coincidente. La primera vez que se llama a este método, guarda el valor de la propiedad <xref:Microsoft.Office.Core._CustomXMLPart.Id%2A> a la cadena `employeeXMLPartID`. El valor de la cadena `employeeXMLPartID` se conserva en el documento porque se declaró mediante el atributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#4](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#4)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#4](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#4)]  
  
## <a name="bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>Enlazar los controles de contenido a elementos en el elemento XML personalizado  
 Enlazar cada control de contenido a un elemento en el elemento XML personalizado mediante la **XMLMapping** propiedad de cada control de contenido.  
  
### <a name="to-bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>Para enlazar los controles de contenido a elementos en el elemento XML personalizado  
  
1.  Agregue el método siguiente a la clase `ThisDocument`. Este método enlaza cada control de contenido a un elemento en el elemento XML personalizado y establece el formato de visualización de fecha de la <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#5](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#5)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#5](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#5)]  
  
## <a name="run-your-code-when-the-document-is-opened"></a>Ejecutar el código cuando se abre el documento  
 Cree el elemento XML personalizado y enlace los controles personalizados a los datos cuando se abre el documento.  
  
### <a name="to-run-your-code-when-the-document-is-opened"></a>Para ejecutar el código cuando se abra el documento  
  
1.  Agregue el siguiente código al método `ThisDocument_Startup` de la clase `ThisDocument`. Este código obtiene la cadena XML desde el **employees.xml** archivo, agrega la cadena XML a un elemento XML personalizado nuevo en el documento y enlaza los controles de contenido a elementos en el elemento XML personalizado.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#2](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#2](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#2)]  
  
## <a name="test-the-project"></a>El proyecto de prueba  
 Cuando abre el documento, los controles de contenido muestran datos de los elementos en el elemento XML personalizado. Puede hacer clic en el <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> para seleccionar uno de tres valores válidos para el `title` elemento, que se definen en el **employees.xsd** archivo. Si modifica los datos en cualquiera de los controles de contenido, los nuevos valores se guardan en el elemento XML personalizado en el documento.  
  
### <a name="to-test-the-content-controls"></a>Para probar los controles de contenido  
  
1.  Presione **F5** para ejecutar el proyecto.  
  
2.  Compruebe que la tabla del documento se parece a la siguiente tabla. Cada una de las cadenas en la segunda columna se obtiene a partir de un elemento del elemento XML personalizado del documento.  
  
    |||  
    |-|-|  
    |**Nombre de empleado**|**Karina Leal**|  
    |**Fecha de contratación**|**1 de abril de 1999**|  
    |**Título**|**Administrador**|  
  
3.  Elija la celda situada a la derecha de la **nombre empleado** de celda y escriba un nombre diferente.  
  
4.  Elija la celda situada a la derecha de la **fecha de contratación** de celda y seleccione una fecha diferente en el selector de fecha.  
  
5.  Elija la celda situada a la derecha de la **título** de celda y seleccione un nuevo elemento de la lista desplegable.  
  
6.  Guarde y cierre el documento.  
  
7.  En el Explorador de archivos, abra el *\bin\Debug* carpeta en la ubicación del proyecto.  
  
8.  Abra el menú contextual para **EmployeeControls.docx** y, a continuación, elija **cambiar el nombre**.  
  
9. Nombre del archivo **EmployeeControls.docx.zip**.  
  
     El **EmployeeControls.docx** documento se guarda en formato XML abierto. Al cambiar el nombre de este documento con el *.zip* extensión de nombre de archivo puede examinar el contenido del documento. Para obtener más información sobre Open XML, vea el artículo técnico [formatos de archivo de presentación de XML abiertos de Office (2007)](http://msdn.microsoft.com/96018532-f62c-4da7-bbff-16b96a483fbf).  
  
10. Abra el **EmployeeControls.docx.zip** archivo.  
  
11. Abra el **customXml** carpeta.  
  
12. Abra el menú contextual para **item2.xml** y, a continuación, elija **abierto**.  
  
     Este archivo contiene el elemento XML personalizado que agregó al documento.  
  
13. Compruebe que los elementos `name`, `hireDate`, y `title` contengan los nuevos valores que introdujo en los controles de contenido en el documento.  
  
14. Cerrar la **item2.xml** archivo.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Puede aprender más sobre cómo usar controles de contenido en estos temas:  
  
-   Use todos los controles de contenido disponibles para crear una plantilla. Para obtener más información, consulte [Tutorial: crear una plantilla mediante controles de contenido](../vsto/walkthrough-creating-a-template-by-using-content-controls.md).  
  
-   Modifique los datos de los elementos XML personalizados con el documento cerrado. La próxima vez que el usuario abra el documento, los controles de contenido que estén enlazados a los elementos XML mostrarán los nuevos datos.  
  
-   Utilice los controles de contenido para proteger elementos de un documento. Para obtener más información, consulte [Cómo: proteger elementos de documentos mediante controles de contenido](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).  
  
## <a name="see-also"></a>Vea también  
 [Automatizar Word usando objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [Controles de contenido](../vsto/content-controls.md)   
 [Cómo: agregar controles de contenido a documentos de Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Cómo: proteger elementos de documentos mediante controles de contenido](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)   
 [Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitaciones de programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  