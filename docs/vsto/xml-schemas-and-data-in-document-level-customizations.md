---
title: Esquemas y datos XML en personalizaciones de nivel de documento
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
ms.openlocfilehash: eb8bc9b9d3149112517d893cd3a704826b6d92d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842843"
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>Esquemas y datos XML en personalizaciones de nivel de documento
  **Importante** La información configurada en este tema con respecto a Microsoft Word se presenta exclusivamente para la ventaja y el uso de las personas y organizaciones que se encuentran fuera del Estados Unidos y de sus territorios, o bien el desarrollo de programas que se ejecutan en, productos de Microsoft Word con licencia de Microsoft antes de la 2010 de enero, cuando Microsoft quitó una implementación de funcionalidad específica relacionada con XML personalizado de Es posible que la información relativa a Microsoft Word no sea leída ni utilizada por personas u organizaciones en el Estados Unidos ni en sus territorios que utilicen o desarrollen programas que se ejecutan en, productos de Microsoft Word con licencia de Microsoft a partir del 10 de enero de 2010; Estos productos no se comportarán igual que los productos con licencia antes de esa fecha o adquiridos y con licencia para usarlos fuera del Estados Unidos.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Microsoft Office Excel y Microsoft Office Word proporcionan la capacidad de asignar esquemas a los documentos. Esta característica puede simplificar la importación y exportación de datos XML dentro y fuera del documento.

 Visual Studio expone elementos de esquema asignados en personalizaciones de nivel de documento como controles en el modelo de programación. En Excel, Visual Studio agrega compatibilidad para enlazar los controles a los datos de bases de datos, servicios web y objetos. Para Word y Excel, Visual Studio agrega compatibilidad con los paneles de acciones, que se pueden usar con un documento asignado a un esquema para crear una experiencia de usuario final mejorada para las soluciones. Para obtener más información, vea [información general del panel de acciones](../vsto/actions-pane-overview.md).

> [!NOTE]
> No puede utilizar esquemas XML de varias partes en soluciones de Excel.

## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>Objetos creados cuando los esquemas se asocian a libros de Excel
 Al adjuntar un esquema a un libro, Visual Studio crea automáticamente varios objetos y los agrega al proyecto. Estos objetos no se deben eliminar con Visual Studio Tools, ya que se administran con Excel. Para eliminarlos, quite los elementos asignados de la hoja de cálculo o desasocie el esquema mediante las herramientas de Excel.

 Hay dos objetos principales:

- Esquema XML (archivo XSD). Para cada esquema del libro, Visual Studio agrega un esquema al proyecto. Aparece como un elemento de proyecto con una extensión XSD en **Explorador de soluciones**.

- Clase <xref:System.Data.DataSet> con tipo. Esta clase se crea basándose en el esquema. Esta clase de conjunto de DataSet es visible en **vista de clases**.

## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>Objetos creados cuando se asignan elementos de esquema a hojas de cálculo de Excel
 Cuando se asigna un elemento de esquema desde el panel de tareas **origen de XML** a una hoja de cálculo, Visual Studio crea automáticamente varios objetos y los agrega al proyecto:

- Controles. Para cada objeto asignado del libro, <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> se crea un control (para los elementos de esquema que no son de repetición) o un <xref:Microsoft.Office.Tools.Excel.ListObject> control (para los elementos de esquema de repetición) en el modelo de programación. El <xref:Microsoft.Office.Tools.Excel.ListObject> control solo se puede eliminar eliminando las asignaciones y los objetos asignados del libro. Para obtener más información sobre los controles, consulte [información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md).

- BindingSource. Cuando se crea una <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> asignando un elemento de esquema que no es de repetición a la hoja de cálculo, <xref:System.Windows.Forms.BindingSource> se crea un y el <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control se enlaza a <xref:System.Windows.Forms.BindingSource> . Debe enlazar <xref:System.Windows.Forms.BindingSource> a una instancia del origen de datos que coincida con el esquema asignado al documento, como una instancia de la clase con tipo <xref:System.Data.DataSet> que se ha creado. Cree el enlace estableciendo las <xref:System.Windows.Forms.BindingSource.DataSource%2A> propiedades y <xref:System.Windows.Forms.BindingSource.DataMember%2A> , que se exponen en la ventana **propiedades** .

    > [!NOTE]
    > <xref:System.Windows.Forms.BindingSource>No se crea para <xref:Microsoft.Office.Tools.Excel.ListObject> objetos. Debe enlazar manualmente <xref:Microsoft.Office.Tools.Excel.ListObject> con el origen de datos estableciendo las <xref:System.Windows.Forms.BindingSource.DataSource%2A> propiedades y <xref:System.Windows.Forms.BindingSource.DataMember%2A> en la ventana **propiedades** .

### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>Esquemas asignados a Office y la ventana orígenes de datos de Visual Studio
 Tanto la funcionalidad de esquemas asignada de Office como la ventana **orígenes de datos** de Visual Studio pueden ayudarle a presentar los datos en una hoja de cálculo de Excel para crear informes o editarlos. En ambos casos, puede arrastrar elementos de datos a la hoja de cálculo de Excel. Ambos métodos crean controles que están enlazados a datos a través de un <xref:System.Windows.Forms.BindingSource> a un origen de datos como un <xref:System.Data.DataSet> o un servicio Web.

> [!NOTE]
> Al asignar un elemento de esquema repetitivo a una hoja de cálculo, Visual Studio crea un <xref:Microsoft.Office.Tools.Excel.ListObject> . <xref:Microsoft.Office.Tools.Excel.ListObject>No se enlaza automáticamente a los datos a través de <xref:System.Windows.Forms.BindingSource> . Debe enlazar manualmente <xref:Microsoft.Office.Tools.Excel.ListObject> con el origen de datos estableciendo las <xref:System.Windows.Forms.BindingSource.DataSource%2A> propiedades y <xref:System.Windows.Forms.BindingSource.DataMember%2A> en la ventana **propiedades** .

 En la tabla siguiente se muestran algunas de las diferencias entre los dos métodos.

|esquema XML|Ventana de orígenes de datos|
|----------------|-------------------------|
|Usa la interfaz de Office.|Usa la ventana **orígenes de datos** en Visual Studio.|
|Habilita las características integradas de Office para importar y exportar datos de archivos XML.|Debe proporcionar la funcionalidad de importación y exportación mediante programación.|
|Debe escribir código para rellenar los controles generados con datos.|Los controles agregados desde la ventana **orígenes de datos** tienen código generado automáticamente para rellenarlos, junto con las cadenas de conexión necesarias cuando se usan servidores de bases de datos.|

## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>Comportamiento cuando los esquemas se adjuntan a documentos de Word
 Los objetos de datos no se crean al adjuntar un esquema a un documento de Word que se utiliza en un proyecto de Office de nivel de documento. Sin embargo, cuando se asigna un elemento de esquema al documento, se crean controles. El tipo de control depende del tipo de elemento que asigne; los elementos que se repiten generan <xref:Microsoft.Office.Tools.Word.XMLNodes> controles y los elementos no repetidos generan <xref:Microsoft.Office.Tools.Word.XMLNode> controles. Para obtener más información, vea [control XMLNodes](../vsto/xmlnodes-control.md) y [control XmlNode](../vsto/xmlnode-control.md).

## <a name="deployment-of-solutions-that-include-xml-schemas"></a>Implementación de soluciones que incluyen esquemas XML
 Debe crear un instalador para implementar una solución que use un esquema XML que esté asignado a un documento. El instalador debe registrar el esquema en la biblioteca de esquemas en el equipo del usuario. Si no registra el esquema, la solución seguirá funcionando porque Word genera un esquema temporal basado en los elementos que se encuentran en el documento cuando el usuario lo abre. Sin embargo, el usuario no podrá realizar la validación ni guardar el esquema que se usó para crear el proyecto. Para obtener más información acerca de los instaladores, vea [implementar aplicaciones, servicios y componentes](../deployment/deploying-applications-services-and-components.md).

 También puede agregar código al proyecto para comprobar si el esquema se encuentra en la biblioteca y se ha registrado. Si no es así, puede advertir al usuario.

 [!code-vb[Trin_VstcoreDataWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstcoreDataWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs#1)]

## <a name="see-also"></a>Vea también

- [Cómo: asignar esquemas a documentos de Word en Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Cómo: asignar esquemas a hojas de cálculo en Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
