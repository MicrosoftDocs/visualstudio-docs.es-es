---
title: "Tutorial: Crear una plantilla mediante controles de contenido"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "bloques de creación [desarrollo de Office en Visual Studio]"
  - "controles de contenido [desarrollo de Office en Visual Studio], agregar a documentos"
  - "Word [desarrollo de Office en Visual Studio], crear documentos"
ms.assetid: 88fb9a60-dcc3-4a5f-a8c9-7aff01ca4b4b
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Tutorial: Crear una plantilla mediante controles de contenido
  Este tutorial muestra cómo crear una personalización de nivel de documento que usa controles de contenido para crear contenido estructurado y reutilizable en una plantilla de Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Word permite crear una colección de elementos de documento reutilizables, llamados *bloques de creación*.  Este tutorial muestra cómo crear dos tablas como bloques de creación.  Cada tabla contiene varios controles de contenido que pueden contener diferentes tipos de contenido, como texto sin formato o fechas.  Una de las tablas contiene información sobre un empleado y la otra tabla contiene los comentarios del cliente.  
  
 Después de crear un documento a partir de la plantilla, puede agregar cualquiera de las tablas al documento usando varios objetos <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl>, que muestran los bloques de creación disponibles en la plantilla.  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Crear tablas que contienen controles de contenido en una plantilla de Word en tiempo de diseño.  
  
-   Rellenar un control de contenido de cuadro combinado y un control de contenido de lista desplegable mediante programación.  
  
-   Impedir que los usuarios editen una tabla especificada.  
  
-   Agregar tablas a la colección de bloques de creación de una plantilla.  
  
-   Crear un control de contenido que muestra los bloques de creación disponibles en la plantilla.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## Crear un nuevo proyecto de plantilla de Word  
 Cree una plantilla de Word para que los usuarios pueden crear fácilmente sus propias copias.  
  
#### Para crear un nuevo proyecto de plantilla de Word  
  
1.  Cree un proyecto de plantilla de Word llamado MyBuildingBlockTemplate.  En el asistente, cree un nuevo documento en la solución.  Para obtener más información, consulte [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] abre la nueva plantilla de Word en el diseñador y agrega el proyecto **MyBuildingBlockTemplate** al **Explorador de soluciones**.  
  
## Crear la tabla de empleados  
 Cree una tabla que contenga cuatro tipos diferentes de controles de contenido donde el usuario pueda escribir información sobre un empleado.  
  
#### Para crear la tabla de empleados  
  
1.  En la plantilla de Word hospedada en el diseñador de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], en la cinta de opciones, haga clic en la pestaña **Insertar**.  
  
2.  En el grupo **Tablas**, haga clic en **Tabla** e inserte una tabla con dos columnas y cuatro filas.  
  
3.  Escriba texto en la primera columna de modo que se parezca a la siguiente columna:  
  
    ||  
    |-|  
    |Nombre de empleado|  
    |Fecha de contratación|  
    |Título|  
    |Imagen|  
  
4.  Haga clic en la primera celda de la segunda columna \(junto a **Nombre de empleado**\).  
  
5.  En la cinta de opciones, haga clic en la pestaña **Desarrollador**.  
  
    > [!NOTE]  
    >  Si la pestaña **Desarrollador** no está visible, primero debe mostrarla.  Para obtener más información, consulte [Cómo: Mostrar la pestaña Programador en la cinta de opciones](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
6.  En el grupo **Controles**, haga clic en el botón **Texto** ![PlainTextContentControl](~/docs/vsto/media/plaintextcontrol.gif "PlainTextContentControl") para agregar <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> a la primera celda.  
  
7.  Haga clic en la segunda celda de la segunda columna \(junto a **Fecha de contratación**\).  
  
8.  En el grupo **Controles**, haga clic en el botón **Selector de fecha** ![DatePickerContentControl](~/docs/vsto/media/datepicker.gif "DatePickerContentControl") para agregar <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> a la segunda celda.  
  
9. Haga clic en la tercera celda de la segunda columna \(junto a **Puesto**\).  
  
10. En el grupo **Controles**, haga clic en el botón **Cuadro combinado** ![ComboBoxContentControl](~/docs/vsto/media/combobox.gif "ComboBoxContentControl") para agregar <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> a la tercera celda.  
  
11. Haga clic en la última celda de la segunda columna \(junto a **Imagen**\).  
  
12. En el grupo **Controles**, haga clic en el botón **Control de contenido de imagen** ![PictureContentControl](~/docs/vsto/media/pictcontentcontrol.gif "PictureContentControl") para agregar <xref:Microsoft.Office.Tools.Word.PictureContentControl> a la última celda.  
  
## Crear la tabla de comentarios de clientes  
 Cree una tabla que contenga tres tipos diferentes de controles de contenido donde el usuario pueda escribir información sobre los comentarios de los clientes.  
  
#### Para crear la tabla de comentarios de clientes  
  
1.  En la plantilla de Word, haga clic en la línea que aparece después de la tabla de empleados que agregó anteriormente y presione ENTRAR para agregar un párrafo nuevo.  
  
2.  En la cinta de opciones, haga clic en la pestaña **Insertar**.  
  
3.  En el grupo **Tablas**, haga clic en **Tabla** e inserte una tabla con dos columnas y tres filas.  
  
4.  Escriba texto en la primera columna de modo que se parezca a la siguiente columna:  
  
    ||  
    |-|  
    |Nombre de cliente|  
    |Grado de satisfacción|  
    |Comentarios|  
  
5.  Haga clic en la primera celda de la segunda columna \(junto a **Nombre de cliente**\).  
  
6.  En la cinta de opciones, haga clic en la pestaña **Desarrollador**.  
  
7.  En el grupo **Controles**, haga clic en el botón **Texto** ![PlainTextContentControl](~/docs/vsto/media/plaintextcontrol.gif "PlainTextContentControl") para agregar <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> a la primera celda.  
  
8.  Haga clic en la segunda celda de la segunda columna \(junto a **Grado de satisfacción**\).  
  
9. En el grupo **Controles**, haga clic en el botón **Lista desplegable** ![DropDownListContentControl](~/docs/vsto/media/dropdownlist.gif "DropDownListContentControl") para agregar <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> a la segunda celda.  
  
10. Haga clic en la última celda de la segunda columna \(junto a **Comentarios**\).  
  
11. En el grupo **Controles**, haga clic en el botón **Texto enriquecido** ![RichTextContentControl](~/docs/vsto/media/richtextcontrol.gif "RichTextContentControl") para agregar <xref:Microsoft.Office.Tools.Word.RichTextContentControl> a la última celda.  
  
## Rellenar el cuadro combinado y la lista desplegable mediante programación  
 Puede inicializar los controles de contenido en tiempo de diseño mediante la ventana **Propiedades** en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  También puede inicializarlos en tiempo de ejecución, lo que le permite establecer sus estados iniciales dinámicamente.  En este tutorial, use código para rellenar las entradas de <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> y <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> en tiempo de ejecución para poder ver cómo funcionan estos objetos.  
  
#### Para modificar la interfaz de usuario de los controles de contenido mediante programación  
  
1.  En el **Explorador de soluciones**, haga clic con el botón derecho en **ThisDocument.cs** o **ThisDocument.vb** y luego haga clic en **Ver código**.  
  
2.  Agregue el código siguiente a la clase `ThisDocument`.  Este código declara varios objetos que usará más adelante en este tutorial.  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#1)]  
  
3.  Agregue el siguiente código al método `ThisDocument_Startup` de la clase `ThisDocument`.  Este código agrega entradas a <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> y <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> en las tablas y establece el texto del marcador de posición que se muestra en cada uno de estos controles antes de que el usuario los edite.  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#2)]  
  
## Impedir que los usuarios editen la tabla de empleados  
 Use el objeto <xref:Microsoft.Office.Tools.Word.GroupContentControl> que declaró anteriormente para proteger la tabla de empleados.  Después de proteger la tabla, los usuarios todavía pueden editar los controles de contenido de la tabla.  Sin embargo, no se puede editar el texto de la primera columna ni modificar la tabla de otras maneras, por ejemplo agregando o eliminando filas y columnas.  Para obtener más información sobre cómo usar <xref:Microsoft.Office.Tools.Word.GroupContentControl> para proteger una parte de un documento, consulte [Controles de contenido](../vsto/content-controls.md).  
  
#### Para impedir que los usuarios editen la tabla de empleados  
  
1.  Agregue el código siguiente al método `ThisDocument_Startup` de la clase `ThisDocument` después del código que agregó en el paso anterior.  Este código impide que los usuarios editen la tabla de empleados al colocarla dentro del objeto <xref:Microsoft.Office.Tools.Word.GroupContentControl> que declaró anteriormente.  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#3)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#3)]  
  
## Agregar las tablas a la colección de bloques de creación  
 Agregue las tablas a una colección de bloques de creación de documentos en la plantilla para que los usuarios puedan insertar las tablas creadas en el documento.  Para obtener más información sobre los bloques de creación de documentos, consulte [Controles de contenido](../vsto/content-controls.md).  
  
#### Para agregar las tablas a los bloques de creación en la plantilla  
  
1.  Agregue el código siguiente al método `ThisDocument_Startup` de la clase `ThisDocument` después del código que agregó en el paso anterior.  Este código agrega nuevos bloques de creación que contienen las tablas a la colección Microsoft.Office.Interop.Word.BuildingBlockEntries, que contiene todos los bloques de creación reutilizables de la plantilla.  Los nuevos bloques de creación se definen en una categoría nueva llamada **Información de empleados y clientes** y se asignan al tipo de bloque de creación Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1.  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#4)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#4)]  
  
2.  Agregue el código siguiente al método `ThisDocument_Startup` de la clase `ThisDocument` después del código que agregó en el paso anterior.  Este código elimina las tablas de la plantilla.  Las tablas ya no son necesarias, ya que se agregaron a la galería de bloques de creación reutilizables de la plantilla.  El código sitúa primero el documento en modo de diseño para que se pueda eliminar la tabla de empleados protegida.  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#5)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#5)]  
  
## Crear un control de contenido que muestra los bloques de creación  
 Cree un control de contenido que proporcione acceso a los bloques de creación \(es decir, las tablas\) que creó anteriormente.  Los usuarios pueden hacer clic en este control para agregar las tablas al documento.  
  
#### Para crear un control de contenido que muestra los bloques de creación  
  
1.  Agregue el código siguiente al método `ThisDocument_Startup` de la clase `ThisDocument` después del código que agregó en el paso anterior.  Este código inicializa el objeto <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> que declaró anteriormente.  <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> muestra todos los bloques de creación que se definen en la categoría **Información de empleados y clientes** y que tienen el tipo de bloque de creación Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1.  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#6)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#6)]  
  
## Probar el proyecto  
 Los usuarios pueden hacer clic en los controles de la galería de bloques de creación del documento para insertar la tabla de empleados o la tabla de comentarios de clientes.  Los usuarios pueden escribir o seleccionar las respuestas en los controles de contenido de ambas tablas.  Los usuarios pueden modificar otras partes de la tabla de comentarios de clientes, pero no deben poder modificar otras partes de la tabla de empleados.  
  
#### Para probar la tabla de empleados  
  
1.  Presione F5 para ejecutar el proyecto.  
  
2.  Haga clic en **Elegir el primer bloque de creación** para mostrar el primer control de contenido de la galería de bloques de creación.  
  
3.  Haga clic en la flecha desplegable situada junto al título **Galería personalizada 1** en el control y seleccione la **Tabla de empleados**.  
  
4.  Haga clic en la celda situada a la derecha de la celda Nombre de empleado y escriba un nombre.  
  
     Compruebe que solo puede agregar texto a esta celda.  <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> permite a los usuarios agregar solo texto, no otros tipos de contenido, como una imagen o una tabla.  
  
5.  Haga clic en la celda situada a la derecha de la celda Fecha de contratación y seleccione una fecha en el selector de fecha.  
  
6.  Haga clic en la celda situada a la derecha de la celda Puesto y seleccione uno de los puestos de trabajo de cuadro combinado.  
  
     También puede escribir el nombre de un puesto de trabajo que no está en la lista.  Esto es posible porque <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> permite a los usuarios seleccionar las entradas de una lista o escribir sus propias entradas.  
  
7.  Haga clic en el icono de la celda situada a la derecha de la celda Imagen y busque una imagen para mostrarla.  
  
8.  Intente agregar filas o columnas a la tabla e intente eliminar filas y columnas de la tabla.  Compruebe que no se puede modificar la tabla.  <xref:Microsoft.Office.Tools.Word.GroupContentControl> impide realizar ninguna modificación.  
  
#### Para probar la tabla de comentarios de clientes  
  
1.  Haga clic en **Elegir el segundo bloque de creación** para mostrar el segundo control de contenido de la galería de bloques de creación.  
  
2.  Haga clic en la flecha desplegable situada junto al título **Galería personalizada 1** en el control y seleccione la **Tabla de clientes**.  
  
3.  Haga clic en la celda situada a la derecha de la celda Nombre de cliente y escriba un nombre.  
  
4.  Haga clic en la celda situada a la derecha de la celda Grado de satisfacción y seleccione una de las opciones disponibles.  
  
     Compruebe que no puede escribir una entrada por su cuenta.  <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> permite a los usuarios seleccionar solo las entradas de una lista.  
  
5.  Haga clic en la celda situada a la derecha de la celda Comentarios y escriba algún comentario.  
  
     También puede agregar contenido que no sea texto, como una imagen o una tabla insertada.  Esto es posible porque <xref:Microsoft.Office.Tools.Word.RichTextContentControl> permite a los usuarios agregar contenido que no sea texto.  
  
6.  Compruebe que puede agregar filas o columnas a la tabla y que puede eliminar filas y columnas de la tabla.  Esto es posible porque no protegió la tabla colocándola en <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  
  
7.  Cierre la plantilla.  
  
## Pasos siguientes  
 Puede obtener más información sobre cómo usar controles de contenido en este tema:  
  
-   Enlazar controles de contenido a elementos XML \(también llamados elementos XML personalizados\) que están insertados en un documento.  Para obtener más información, consulte [Tutorial: Enlazar controles de contenido a elementos XML personalizados](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).  
  
## Vea también  
 [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [Controles de contenido](../vsto/content-controls.md)   
 [Cómo: Agregar controles de contenido a documentos de Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Cómo: Proteger elementos de documentos mediante controles de contenido](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  