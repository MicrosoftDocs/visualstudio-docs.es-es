---
title: 'Tutorial: Creación de una plantilla mediante controles de contenido'
description: Obtenga información sobre cómo crear una personalización de nivel de documento que use controles de contenido para crear contenido estructurado y reutilizable en una plantilla de Microsoft Word.
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- building blocks [Office development in Visual Studio]
- Word [Office development in Visual Studio], creating documents
- content controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7f78ca406d19461de7fa8e2a8c147b1003c9c852
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826972"
---
# <a name="walkthrough-create-a-template-by-using-content-controls"></a>Tutorial: Creación de una plantilla mediante controles de contenido
  Este tutorial muestra cómo crear una personalización de nivel de documento que usa controles de contenido para crear contenido estructurado y reutilizable en una plantilla de Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Word permite crear una colección de elementos de documento reutilizables, denominados *bloques de creación*. Este tutorial muestra cómo crear dos tablas como bloques de creación. Cada tabla contiene varios controles de contenido que pueden contener diferentes tipos de contenido, como texto sin formato o fechas. Una de las tablas contiene información sobre un empleado y la otra tabla contiene los comentarios del cliente.

 Después de crear un documento a partir de la plantilla, puede agregar cualquiera de las tablas al documento usando varios objetos <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl>, que muestran los bloques de creación disponibles en la plantilla.

 En este tutorial se muestran las tareas siguientes:

- Crear tablas que contienen controles de contenido en una plantilla de Word en tiempo de diseño.

- Rellenar un control de contenido de cuadro combinado y un control de contenido de lista desplegable mediante programación.

- Impedir que los usuarios editen una tabla especificada.

- Agregar tablas a la colección de bloques de creación de una plantilla.

- Crear un control de contenido que muestra los bloques de creación disponibles en la plantilla.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-a-new-word-template-project"></a>Creación de un proyecto de plantilla de Word
 Cree una plantilla de Word para que los usuarios pueden crear fácilmente sus propias copias.

### <a name="to-create-a-new-word-template-project"></a>Para crear un nuevo proyecto de plantilla de Word

1. Cree un proyecto de plantilla de Word con el nombre **MyBuildingBlockTemplate**. En el asistente, cree un nuevo documento en la solución. Para obtener más información, [vea Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] abre la nueva plantilla de Word en el diseñador y agrega el **proyecto MyBuildingBlockTemplate** **a Explorador de soluciones**.

## <a name="create-the-employee-table"></a>Creación de la tabla employee
 Cree una tabla que contenga cuatro tipos diferentes de controles de contenido donde el usuario pueda escribir información sobre un empleado.

### <a name="to-create-the-employee-table"></a>Para crear la tabla de empleados

1. En la plantilla de Word hospedada en el diseñador, en la [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] cinta de opciones, haga clic en **la pestaña** Insertar.

2. En el **grupo Tablas** , haga clic **en Tabla** e inserte una tabla con dos columnas y cuatro filas.

3. Escriba texto en la primera columna de modo que se parezca a la siguiente columna:

   ||
   |-|
   |**Nombre de empleado**|
   |**Fecha de contratación**|
   |**Título**|
   |**Imagen**|

4. Haga clic en la primera celda de la segunda columna (junto a **Nombre del empleado).**

5. En la cinta de opciones, haga clic en la pestaña **Desarrollador** .

   > [!NOTE]
   > Si la pestaña **Desarrollador** no está visible, primero debe mostrarla. Para obtener más información, [vea Cómo: Mostrar la pestaña para desarrolladores en la cinta de opciones](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

6. En el **grupo Controles** , haga clic en el **botón Texto** ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") para agregar un elemento a <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> la primera celda.

7. Haga clic en la segunda celda de la segunda columna (junto a **Fecha de contratación).**

8. En el **grupo Controles** , haga clic en el **botón Selector** de fecha ![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl") para agregar un a <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> la segunda celda.

9. Haga clic en la tercera celda de la segunda columna (junto a **Título).**

10. En el **grupo Controles** , haga clic en el botón **Cuadro combinado** ![ComboBoxContentControl](../vsto/media/combobox.gif "ComboBoxContentControl") para agregar un elemento a <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> la tercera celda.

11. Haga clic en la última celda de la segunda columna (junto a **Imagen).**

12. En el **grupo Controles,** haga clic en el botón **Control de** contenido de imagen ![PictureContentControl](../vsto/media/pictcontentcontrol.gif "PictureContentControl") para agregar a <xref:Microsoft.Office.Tools.Word.PictureContentControl> la última celda.

## <a name="create-the-customer-feedback-table"></a>Creación de la tabla de comentarios de los clientes
 Cree una tabla que contenga tres tipos diferentes de controles de contenido donde el usuario pueda escribir información sobre los comentarios de los clientes.

### <a name="to-create-the-customer-feedback-table"></a>Para crear la tabla de comentarios de clientes

1. En la plantilla de Word, haga clic en la línea después de la tabla employee que agregó anteriormente y presione **Entrar** para agregar un párrafo nuevo.

2. En la cinta de opciones, haga clic **en la pestaña** Insertar.

3. En el **grupo Tablas** , haga clic **en Tabla** e inserte una tabla con dos columnas y tres filas.

4. Escriba texto en la primera columna de modo que se parezca a la siguiente columna:

   ||
   |-|
   |**Nombre del cliente**|
   |**Grado de satisfacción**|
   |**Comentarios**|

5. Haga clic en la primera celda de la segunda columna (junto a **Nombre del cliente).**

6. En la cinta de opciones, haga clic en la pestaña **Desarrollador** .

7. En el **grupo Controles,** haga clic en **el botón Texto** ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") para agregar a <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> la primera celda.

8. Haga clic en la segunda celda de la segunda columna (junto a **Clasificación de satisfacción).**

9. En el **grupo Controles,** haga clic en **el botón Lista** desplegable ![DropDownListContentControl](../vsto/media/dropdownlist.gif "DropDownListContentControl") para agregar un elemento a <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> la segunda celda.

10. Haga clic en la última celda de la segunda columna (junto a **Comentarios**).

11. En el **grupo Controles,** haga clic en el **botón Texto enriquecido** ![RichTextContentControl](../vsto/media/richtextcontrol.gif "RichTextContentControl") para agregar a <xref:Microsoft.Office.Tools.Word.RichTextContentControl> la última celda.

## <a name="populate-the-combo-box-and-drop-down-list-programmatically"></a>Rellenar el cuadro combinado y la lista desplegable mediante programación
 Puede inicializar controles de contenido en tiempo de diseño mediante la **ventana Propiedades** de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . También puede inicializarlos en tiempo de ejecución, lo que le permite establecer sus estados iniciales dinámicamente. En este tutorial, use código para rellenar las entradas de y en tiempo de ejecución para que pueda ver cómo <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> funcionan estos objetos.

### <a name="to-modify-the-ui-of-the-content-controls-programmatically"></a>Para modificar la interfaz de usuario de los controles de contenido mediante programación

1. En **Explorador de soluciones**, haga clic con el botón derecho **en ThisDocument.cs** o **ThisDocument.vb** y, a continuación, haga clic **en Ver código.**

2. Agregue el siguiente código a la clase `ThisDocument` . Este código declara varios objetos que usará más adelante en este tutorial.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs" id="Snippet1":::

3. Agregue el siguiente código al método `ThisDocument_Startup` de la clase `ThisDocument`. Este código agrega entradas a <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> y <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> en las tablas y establece el texto del marcador de posición que se muestra en cada uno de estos controles antes de que el usuario los edite.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs" id="Snippet2":::

## <a name="prevent-users-from-editing-the-employee-table"></a>Impedir que los usuarios editen la tabla de empleados
 Use el objeto <xref:Microsoft.Office.Tools.Word.GroupContentControl> que declaró anteriormente para proteger la tabla de empleados. Después de proteger la tabla, los usuarios todavía pueden editar los controles de contenido de la tabla. Sin embargo, no se puede editar el texto de la primera columna ni modificar la tabla de otras maneras, por ejemplo agregando o eliminando filas y columnas. Para obtener más información sobre cómo usar para <xref:Microsoft.Office.Tools.Word.GroupContentControl> proteger una parte de un documento, vea Controles de [contenido](../vsto/content-controls.md).

### <a name="to-prevent-users-from-editing-the-employee-table"></a>Para impedir que los usuarios editen la tabla de empleados

1. Agregue el código siguiente al método `ThisDocument_Startup` de la clase `ThisDocument` después del código que agregó en el paso anterior. Este código impide que los usuarios editen la tabla de empleados al colocarla dentro del objeto <xref:Microsoft.Office.Tools.Word.GroupContentControl> que declaró anteriormente.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs" id="Snippet3":::

## <a name="add-the-tables-to-the-building-block-collection"></a>Agregar las tablas a la colección de bloques de creación
 Agregue las tablas a una colección de bloques de creación de documentos en la plantilla para que los usuarios puedan insertar las tablas creadas en el documento. Para obtener más información sobre los bloques de creación de documentos, vea [Controles de contenido.](../vsto/content-controls.md)

### <a name="to-add-the-tables-to-the-building-blocks-in-the-template"></a>Para agregar las tablas a los bloques de creación en la plantilla

1. Agregue el código siguiente al método `ThisDocument_Startup` de la clase `ThisDocument` después del código que agregó en el paso anterior. Este código agrega nuevos bloques de creación que contienen las tablas a la colección Microsoft.Office.Interop.Word.BuildingBlockEntries, que contiene todos los bloques de creación reutilizables de la plantilla. Los nuevos bloques de creación se definen en una nueva categoría denominada **Employee and Customer Information** y se les asigna el tipo de bloque de creación `Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs" id="Snippet4":::

2. Agregue el código siguiente al método `ThisDocument_Startup` de la clase `ThisDocument` después del código que agregó en el paso anterior. Este código elimina las tablas de la plantilla. Las tablas ya no son necesarias, ya que se agregaron a la galería de bloques de creación reutilizables de la plantilla. El código sitúa primero el documento en modo de diseño para que se pueda eliminar la tabla de empleados protegida.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs" id="Snippet5":::

## <a name="create-a-content-control-that-displays-the-building-blocks"></a>Crear un control de contenido que muestre los bloques de creación
 Cree un control de contenido que proporcione acceso a los bloques de creación (es decir, las tablas) que creó anteriormente. Los usuarios pueden hacer clic en este control para agregar las tablas al documento.

### <a name="to-create-a-content-control-that-displays-the-building-blocks"></a>Para crear un control de contenido que muestra los bloques de creación

1. Agregue el código siguiente al método `ThisDocument_Startup` de la clase `ThisDocument` después del código que agregó en el paso anterior. Este código inicializa el objeto <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> que declaró anteriormente. muestra <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> todos los bloques de creación definidos en la categoría **Employee and Customer Information** y que tienen el tipo de bloque de creación `Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb" id="Snippet6":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs" id="Snippet6":::

## <a name="test-the-project"></a>Prueba del proyecto
 Los usuarios pueden hacer clic en los controles de la galería de bloques de creación del documento para insertar la tabla de empleados o la tabla de comentarios de clientes. Los usuarios pueden escribir o seleccionar las respuestas en los controles de contenido de ambas tablas. Los usuarios pueden modificar otras partes de la tabla de comentarios de clientes, pero no deben poder modificar otras partes de la tabla de empleados.

### <a name="to-test-the-employee-table"></a>Para probar la tabla de empleados

1. Presione **F5** para ejecutar el proyecto.

2. Haga **clic en Elegir el primer bloque de creación para** mostrar el primer control de contenido de la galería de bloques de creación.

3. Haga clic en la flecha desplegable situada junto al encabezado **Galería personalizada 1** del control y seleccione **Tabla de empleados**.

4. Haga clic en la celda a la derecha de la **celda Employee Name (Nombre** del empleado) y escriba un nombre.

     Compruebe que solo puede agregar texto a esta celda. <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> permite a los usuarios agregar solo texto, no otros tipos de contenido, como una imagen o una tabla.

5. Haga clic en la celda a la derecha de la celda **Hire Date (Fecha** de contratación) y seleccione una fecha en el selector de fechas.

6. Haga clic en la celda a la derecha de la **celda Título** y seleccione uno de los títulos de trabajo en el cuadro combinado.

     También puede escribir el nombre de un puesto de trabajo que no está en la lista. Esto es posible porque <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> permite a los usuarios seleccionar las entradas de una lista o escribir sus propias entradas.

7. Haga clic en el icono de la celda a la derecha de la celda **Imagen** y vaya a una imagen para mostrarla.

8. Intente agregar filas o columnas a la tabla e intente eliminar filas y columnas de la tabla. Compruebe que no se puede modificar la tabla. <xref:Microsoft.Office.Tools.Word.GroupContentControl> impide realizar ninguna modificación.

### <a name="to-test-the-customer-feedback-table"></a>Para probar la tabla de comentarios de clientes

1. Haga **clic en Elegir el segundo bloque de creación para** mostrar el segundo control de contenido de la galería de bloques de creación.

2. Haga clic en la flecha desplegable situada junto al encabezado **Galería personalizada 1** del control y seleccione **Tabla de clientes**.

3. Haga clic en la celda a la derecha de la celda **Nombre del** cliente y escriba un nombre.

4. Haga clic en la celda a la derecha de la celda **Clasificación de satisfacción** y seleccione una de las opciones disponibles.

     Compruebe que no puede escribir una entrada por su cuenta. <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> permite a los usuarios seleccionar solo las entradas de una lista.

5. Haga clic en la celda a la derecha de la **celda Comentarios** y escriba algunos comentarios.

     También puede agregar contenido que no sea texto, como una imagen o una tabla insertada. Esto es posible porque <xref:Microsoft.Office.Tools.Word.RichTextContentControl> permite a los usuarios agregar contenido que no sea texto.

6. Compruebe que puede agregar filas o columnas a la tabla y que puede eliminar filas y columnas de la tabla. Esto es posible porque no protegió la tabla colocándola en <xref:Microsoft.Office.Tools.Word.GroupContentControl>.

7. Cierre la plantilla.

## <a name="next-steps"></a>Pasos siguientes
 Puede obtener más información sobre cómo usar controles de contenido en este tema:

- Enlazar controles de contenido a elementos XML (también llamados elementos XML personalizados) que están insertados en un documento. Para obtener más información, vea [Tutorial: Enlazar controles de contenido a elementos XML personalizados.](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)

## <a name="see-also"></a>Consulte también
- [Automatización de Word mediante objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)
- [Controles de contenido](../vsto/content-controls.md)
- [Cómo: Agregar controles de contenido a documentos de Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Cómo: Proteger partes de documentos mediante controles de contenido](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)
- [Introducción a los elementos host y los controles host](../vsto/host-items-and-host-controls-overview.md)
- [Limitaciones de programación de los elementos host y los controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)
