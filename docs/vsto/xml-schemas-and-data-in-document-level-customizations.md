---
title: Esquemas XML y datos en personalizaciones de nivel de documento
description: Microsoft Excel y Word proporcionan la capacidad de asignar esquemas a los documentos y pueden simplificar la importación y exportación de datos XML dentro y fuera del documento.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 54e993f41787cfa44bb0aaa78cc7aff8fbad53d8
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826595"
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>Esquemas y datos XML en personalizaciones de nivel de documento
  **Importante** La información que se establece en este tema sobre Microsoft Word se presenta exclusivamente para beneficio y uso de personas y organizaciones que se encuentran fuera de Estados Unidos y sus territorios o que usan o desarrollan programas que se ejecutan en productos de Microsoft Word con licencia de Microsoft antes de enero de 2010, cuando Microsoft quitó una implementación de funcionalidad determinada relacionada con XML personalizado de Microsoft Word. Esta información relativa a Microsoft Word no puede ser leida ni usada por personas u organizaciones de la Estados Unidos o sus territorios que usan o desarrollan programas que se ejecutan en productos de Microsoft Word con licencia de Microsoft a partir del 10 de enero de 2010. esos productos no se comportarán igual que los productos con licencia antes de esa fecha o adquiridos y con licencia para su uso fuera del Estados Unidos.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Microsoft Office Excel y Microsoft Office Word proporcionan la capacidad de asignar esquemas a los documentos. Esta característica puede simplificar la importación y exportación de datos XML dentro y fuera del documento.

 Visual Studio expone elementos de esquema asignados en personalizaciones de nivel de documento como controles en el modelo de programación. Para Excel, Visual Studio compatibilidad para enlazar los controles a datos de bases de datos, servicios web y objetos. Para Word y Excel, Visual Studio agrega compatibilidad con los paneles de acciones, que se pueden usar con un documento asignado a esquemas para crear una experiencia mejorada del usuario final para las soluciones. Para obtener más información, vea Información [general del panel Acciones.](../vsto/actions-pane-overview.md)

> [!NOTE]
> No se pueden usar esquemas XML de varias partes en soluciones de Excel.

## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>Objetos creados cuando se adjuntan esquemas a libros de Excel
 Al adjuntar un esquema a un libro, Visual Studio automáticamente varios objetos y los agrega al proyecto. Estos objetos no deben eliminarse mediante Visual Studio, ya que están administrados por Excel. Para eliminarlos, quite los elementos asignados de la hoja de cálculo o desasoyéquelo mediante herramientas de Excel.

 Hay dos objetos principales:

- Esquema XML (archivo XSD). Para cada esquema del libro, Visual Studio agrega un esquema al proyecto. Aparece como un elemento de proyecto con una extensión XSD **en Explorador de soluciones**.

- Clase <xref:System.Data.DataSet> con tipo. Esta clase se crea en función del esquema. Esta clase de conjunto de datos es visible **en Vista de clases**.

## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>Objetos creados cuando los elementos de esquema se asignan a hojas de cálculo de Excel
 Al asignar un elemento de esquema desde el panel de tareas Origen **XML** a una hoja de cálculo, Visual Studio automáticamente crea varios objetos y los agrega al proyecto:

- Controles. Para cada objeto asignado del libro, se crea un control (para elementos de esquema no repetitivos) o un control (para repetir elementos de esquema) en el <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> <xref:Microsoft.Office.Tools.Excel.ListObject> modelo de programación. El <xref:Microsoft.Office.Tools.Excel.ListObject> control solo se puede eliminar eliminando las asignaciones y los objetos asignados del libro. Para obtener más información sobre los controles, vea [Host items and host controls overview](../vsto/host-items-and-host-controls-overview.md).

- Bindingsource. Cuando se crea un mediante la asignación de un elemento de esquema que no se repite a la hoja de cálculo, se crea y el <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control se enlaza a <xref:System.Windows.Forms.BindingSource> <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> <xref:System.Windows.Forms.BindingSource> . Debe enlazar a una instancia del origen de datos que coincida con el esquema asignado al documento, como una instancia de la clase con tipo que <xref:System.Windows.Forms.BindingSource> <xref:System.Data.DataSet> se creó. Cree el enlace estableciendo las <xref:System.Windows.Forms.BindingSource.DataSource%2A> propiedades y , que se exponen en la <xref:System.Windows.Forms.BindingSource.DataMember%2A> **ventana** Propiedades.

    > [!NOTE]
    > no <xref:System.Windows.Forms.BindingSource> se crea para los objetos <xref:Microsoft.Office.Tools.Excel.ListObject> . Debe enlazar manualmente al origen de <xref:Microsoft.Office.Tools.Excel.ListObject> datos estableciendo las propiedades <xref:System.Windows.Forms.BindingSource.DataSource%2A> y en la <xref:System.Windows.Forms.BindingSource.DataMember%2A> **ventana** Propiedades.

### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>Esquemas asignados a Office y la ventana Visual Studio orígenes de datos
 Tanto la funcionalidad de esquema asignada de Office como la ventana Visual Studio **Data Sources** (Orígenes de datos) pueden ayudarle a presentar datos en una hoja de cálculo de Excel para informes o edición. En ambos casos, puede arrastrar elementos de datos a la hoja de cálculo de Excel. Ambos métodos crean controles que están enlazados a datos a través de a un origen de <xref:System.Windows.Forms.BindingSource> datos como o un servicio <xref:System.Data.DataSet> web.

> [!NOTE]
> Al asignar un elemento de esquema que se repite a una hoja de cálculo, Visual Studio crea un <xref:Microsoft.Office.Tools.Excel.ListObject> . no <xref:Microsoft.Office.Tools.Excel.ListObject> se enlaza automáticamente a los datos a través de <xref:System.Windows.Forms.BindingSource> . Debe enlazar manualmente al origen de datos <xref:Microsoft.Office.Tools.Excel.ListObject> estableciendo las <xref:System.Windows.Forms.BindingSource.DataSource%2A> propiedades y en la <xref:System.Windows.Forms.BindingSource.DataMember%2A> **ventana** Propiedades.

 En la tabla siguiente se muestran algunas de las diferencias entre los dos métodos.

|Esquema XML|Ventana de orígenes de datos|
|----------------|-------------------------|
|Usa la interfaz de Office.|Usa **la ventana Orígenes** de datos Visual Studio.|
|Habilita las características integradas de Office para importar y exportar datos desde archivos XML.|Debe proporcionar la funcionalidad de importación y exportación mediante programación.|
|Debe escribir código para rellenar los controles generados con datos.|Los controles agregados desde la **ventana Orígenes** de datos tienen código generado automáticamente para rellenarlos, junto con las cadenas de conexión necesarias cuando se usan servidores de base de datos.|

## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>Comportamiento cuando los esquemas se adjuntan a documentos de Word
 Los objetos de datos no se crean al adjuntar un esquema a un documento de Word que se usa en un proyecto de Office de nivel de documento. Sin embargo, al asignar un elemento de esquema al documento, se crean controles. El tipo de control depende del tipo de elemento que asigne; los elementos repetidos <xref:Microsoft.Office.Tools.Word.XMLNodes> generan controles y los elementos que no se repiten generan <xref:Microsoft.Office.Tools.Word.XMLNode> controles. Para obtener más información, [vea CONTROL XMLNodes y](../vsto/xmlnodes-control.md) CONTROL [XMLNode](../vsto/xmlnode-control.md).

## <a name="deployment-of-solutions-that-include-xml-schemas"></a>Implementación de soluciones que incluyen esquemas XML
 Debe crear un instalador para implementar una solución que use un esquema XML asignado a un documento. El instalador debe registrar el esquema en la biblioteca de esquemas en el equipo del usuario. Si no registra el esquema, la solución seguirá funcionando porque Word genera un esquema temporal basado en los elementos que se encuentran en el documento cuando el usuario lo abre. Sin embargo, el usuario no podrá realizar la validación en o guardar el esquema que se usó para crear el proyecto. Para obtener más información sobre los instaladores, vea [Implementar aplicaciones, servicios y componentes.](../deployment/deploying-applications-services-and-components.md)

 También puede agregar código al proyecto para comprobar si el esquema está en la biblioteca y está registrado. Si no es así, puede advertir al usuario.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs" id="Snippet1":::

## <a name="see-also"></a>Consulte también

- [Cómo: Asignar esquemas a documentos de Word dentro de Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Cómo: Asignar esquemas a hojas de cálculo dentro de Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
