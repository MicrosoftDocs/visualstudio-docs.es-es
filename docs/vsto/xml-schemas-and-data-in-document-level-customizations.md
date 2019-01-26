---
title: Esquemas y datos en las personalizaciones de nivel de documento XML
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio]
- schemas [Office development in Visual Studio]
- XML [Office development in Visual Studio], XML schemas
- XML schemas [Office development in Visual Studio], about XML schemas and data
- Office development in Visual Studio, XML
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d2959707048cb3223b6866c3c8aa4c04cc146077
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875463"
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>Esquemas y datos en las personalizaciones de nivel de documento XML
  **Importante** la información en este tema con respecto a Microsoft Word se presenta exclusivamente para el uso y disfrute de individuos y organizaciones que se encuentran fuera de Estados Unidos y sus territorios o quién está usando o desarrollo programas que se ejecutan en, los productos de Microsoft Word que se licencia de Microsoft antes de enero de 2010, cuando Microsoft quita una implementación de la funcionalidad concreta relacionadas con XML personalizado de Microsoft Word. Esta información con respecto a Microsoft Word no puede ser leída o utilizada por personas u organizaciones en Estados Unidos o en sus territorios que utiliza, o desarrollar programas que se ejecutan en los productos de Microsoft Word que se licencia de Microsoft después de 10 de enero de 2010 ; los productos no comportarán igual que los productos con licencia antes de esa fecha o adquirido y con licencia para su uso fuera de Estados Unidos.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Microsoft Office Excel y Microsoft Office Word proporcionan la capacidad de asignar esquemas a los documentos. Esta característica puede simplificar la importación y exportación de datos XML dentro y fuera del documento.

 Visual Studio expone asigna elementos de esquema en las personalizaciones de nivel de documento como controles en el modelo de programación. Para Excel, Visual Studio agrega compatibilidad para enlazar los controles a datos en las bases de datos, servicios Web y objetos. Para Word y Excel, Visual Studio agrega compatibilidad para paneles de acciones, que puede utilizarse con un documento de esquema asignado para crear una experiencia de usuario final mejorada para sus soluciones. Para obtener más información, consulte [información general sobre el panel de acciones](../vsto/actions-pane-overview.md).

> [!NOTE]
>  No se puede usar los esquemas XML con varias partes en soluciones de Excel.

## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>Objetos creados cuando se asocian esquemas a libros de Excel
 Cuando se adjunta un esquema a un libro, Visual Studio crea varios objetos y agregarlos al proyecto automáticamente. Estos objetos no deben eliminarse mediante herramientas de Visual Studio, ya que son administrados por Excel. Para eliminar los elementos, quite los elementos asignados de la hoja de cálculo o desasocie el esquema mediante el uso de herramientas de Excel.

 Hay dos objetos principales:

-   Esquema XML (archivo XSD). Para cada esquema en el libro, Visual Studio agrega un esquema al proyecto. Esto aparece como un elemento de proyecto con una extensión XSD en **el Explorador de soluciones**.

-   Clase <xref:System.Data.DataSet> con tipo. Esta clase se crea basándose en el esquema. Esta clase de conjunto de datos está visible en **vista de clases**.

## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>Objetos creados cuando se asignan elementos de esquema a hojas de cálculo de Excel
 Cuando se asigna un elemento de esquema desde el **origen XML** panel de tareas a una hoja de cálculo, Visual Studio automáticamente crea varios objetos y las agrega al proyecto:

-   Controles. Para cada objeto asignado en el libro, un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control (para los elementos de esquema no es de repetición) o un <xref:Microsoft.Office.Tools.Excel.ListObject> control (para elementos de esquema que se repiten) se crea en el modelo de programación. El <xref:Microsoft.Office.Tools.Excel.ListObject> control puede eliminarse mediante la eliminación de las asignaciones y los objetos asignados desde el libro. Para obtener más información acerca de los controles, vea [elementos Host y hospedar información general sobre controles](../vsto/host-items-and-host-controls-overview.md).

-   BindingSource. Cuando creas un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> asignando un elemento de esquema no repetitivo a la hoja de cálculo, un <xref:System.Windows.Forms.BindingSource> se crea y el <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> está enlazado el <xref:System.Windows.Forms.BindingSource>. Se debe enlazar la <xref:System.Windows.Forms.BindingSource> a una instancia del origen de datos que coincida con el esquema que se asigna al documento, como una instancia de con tipo <xref:System.Data.DataSet> clase que se creó. Crear el enlace estableciendo el <xref:System.Windows.Forms.BindingSource.DataSource%2A> y <xref:System.Windows.Forms.BindingSource.DataMember%2A> propiedades, que se exponen en el **propiedades** ventana.

    > [!NOTE]
    >  El <xref:System.Windows.Forms.BindingSource> no se creó para <xref:Microsoft.Office.Tools.Excel.ListObject> objetos. Debe enlazar manualmente el <xref:Microsoft.Office.Tools.Excel.ListObject> al origen de datos estableciendo el <xref:System.Windows.Forms.BindingSource.DataSource%2A> y <xref:System.Windows.Forms.BindingSource.DataMember%2A> propiedades en el **propiedades** ventana.

### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>Office asigna esquemas y la ventana de orígenes de datos de Visual Studio
 Tanto la funcionalidad del esquema asignado de Office y Visual Studio **orígenes de datos** ventana puede ayudar a presentar datos en una hoja de cálculo de Excel para crear informes o editar. En ambos casos puede arrastrar elementos de datos a la hoja de cálculo de Excel. Ambos métodos crean controles enlazados a través de un <xref:System.Windows.Forms.BindingSource> a un origen de datos, como un <xref:System.Data.DataSet> o un servicio web.

> [!NOTE]
>  Al asignar un elemento de esquema repetitivo a una hoja de cálculo, Visual Studio crea un <xref:Microsoft.Office.Tools.Excel.ListObject>. El <xref:Microsoft.Office.Tools.Excel.ListObject> no se enlaza automáticamente a los datos a través de la <xref:System.Windows.Forms.BindingSource>. Debe enlazar manualmente el <xref:Microsoft.Office.Tools.Excel.ListObject> al origen de datos estableciendo el <xref:System.Windows.Forms.BindingSource.DataSource%2A> y <xref:System.Windows.Forms.BindingSource.DataMember%2A> propiedades en el **propiedades** ventana.

 La siguiente tabla muestra algunas de las diferencias entre los dos métodos.

|Esquema XML|Ventana de orígenes de datos|
|----------------|-------------------------|
|Usa la interfaz de Office.|Usa **orígenes de datos** ventana de Visual Studio.|
|Habilita las características integradas de Office para importar y exportar datos desde archivos XML.|Debe proporcionar la importación y exportación funcionalidad mediante programación.|
|Debe escribir código para rellenar los controles generados con datos.|Los controles agregados desde la **orígenes de datos** ventana tiene el código generado automáticamente para su relleno, junto con las cadenas de conexión necesarios cuando se usan servidores de base de datos.|

## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>Comportamiento cuando se asocian esquemas a documentos de Word
 No se crean objetos de datos cuando se adjunta un esquema a un documento de Word que se usa en un proyecto de Office de nivel de documento. Sin embargo, al asignar un elemento de esquema en el documento, se crean los controles. El tipo de control depende del tipo de elemento de mapa; generan elementos de repetición <xref:Microsoft.Office.Tools.Word.XMLNodes> controles y elementos no repetitivo generar <xref:Microsoft.Office.Tools.Word.XMLNode> controles. Para obtener más información, consulte [XMLNodes (Control)](../vsto/xmlnodes-control.md) y [XMLNode (Control)](../vsto/xmlnode-control.md).

## <a name="deployment-of-solutions-that-include-xml-schemas"></a>Implementación de soluciones que incluyen los esquemas XML
 Debe crear un instalador para implementar una solución que usa un esquema XML que se asigna a un documento. El instalador debe registrar el esquema en la biblioteca de esquema en el equipo del usuario. Si no registra el esquema, la solución seguirá funcionando porque Word genera un esquema temporal basado en los elementos que se encuentran en el documento cuando el usuario lo abra. Sin embargo, el usuario no podrá realizar la validación frente a o guardar el esquema que se usó para crear el proyecto. Para obtener más información acerca de los instaladores, vea [implementar aplicaciones, servicios y componentes](../deployment/deploying-applications-services-and-components.md).

 También puede agregar código al proyecto para comprobar si el esquema está en la biblioteca registrada. Si no es así, puede advertir al usuario.

 [!code-vb[Trin_VstcoreDataWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstcoreDataWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs#1)]

## <a name="see-also"></a>Vea también

- [Cómo: Asignar esquemas a documentos de Word en Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Cómo: Asignar esquemas a hojas de cálculo en Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
