---
title: Esquemas y datos en las personalizaciones de nivel de documento XML | Documentos de Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio]
- schemas [Office development in Visual Studio]
- XML [Office development in Visual Studio], XML schemas
- XML schemas [Office development in Visual Studio], about XML schemas and data
- Office development in Visual Studio, XML
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: b3f55c8c6b2975e8dbaa85177fddcadaf62e000e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>Esquemas y datos XML en personalizaciones de nivel de documento
  **Importante** la información que figura en este tema con respecto a Microsoft Word está presentado exclusivamente para el beneficio y el uso de personas y organizaciones que se encuentran fuera de Estados Unidos y sus territorios o que está usando, o del desarrollo programas que se ejecutan en, productos de Microsoft Word que se autoriza el uso de Microsoft antes de enero de 2010, cuando Microsoft quita una implementación de funcionalidad concreta relacionada con XML personalizado de Microsoft Word. Esta información con respecto a Microsoft Word no puede leer o utilizada por personas u organizaciones en Estados Unidos o en sus territorios que están usando o desarrollar programas que se ejecutan en productos de Microsoft Word que se usan bajo licencia Microsoft después de 10 de enero de 2010 ; los productos no comportarán igual que los productos con licencia antes de esa fecha o adquirido y licencia para su uso fuera de Estados Unidos.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Microsoft Office Excel y Microsoft Office Word proporcionan la capacidad de asignar esquemas a los documentos. Esta característica puede simplificar la importación y exportación de datos XML en el documento.  
  
 Visual Studio expone asigna elementos de esquema en las personalizaciones de nivel de documento como controles en el modelo de programación. Para Excel, Visual Studio agrega compatibilidad para enlazar los controles a datos en las bases de datos, servicios Web y objetos. Para Word y Excel, Visual Studio agrega compatibilidad para paneles de acciones, que puede utilizarse con un documento de esquema asignado para crear una experiencia de usuario final mejorada para las soluciones. Para obtener más información, consulta [Actions Pane Overview](../vsto/actions-pane-overview.md).  
  
> [!NOTE]  
>  No se puede utilizar esquemas XML compuestos en soluciones de Excel.  
  
## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>Objetos creados cuando se asocian esquemas a libros de Excel  
 Cuando se asocia un esquema a un libro, Visual Studio automáticamente crea varios objetos y los agrega a su proyecto. Estos objetos no deben eliminarse mediante herramientas de Visual Studio, ya que son administrados por Excel. Para eliminarlos, quite los elementos asignados de la hoja de cálculo o desasocie el esquema mediante las herramientas de Excel.  
  
 Hay dos objetos principales:  
  
-   Esquema XML (archivo XSD). Para cada esquema en el libro, Visual Studio agrega un esquema al proyecto. Esto aparece como un elemento de proyecto con una extensión XSD en **el Explorador de soluciones**.  
  
-   Clase <xref:System.Data.DataSet> con tipo. Esta clase se crea basándose en el esquema. Esta clase de conjunto de datos está visible en **vista de clases**.  
  
## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>Objetos creados cuando se asignan elementos de esquema a hojas de cálculo de Excel  
 Cuando se asigna un elemento de esquema de la **origen XML** panel de tareas a una hoja de cálculo, Visual Studio automáticamente crea varios objetos y los agrega al proyecto:  
  
-   Controles. Por cada objeto asignado en el libro, un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control (para los elementos de esquema no repetitivo) o un <xref:Microsoft.Office.Tools.Excel.ListObject> control (para elementos de esquema que se repiten) se crea en el modelo de programación. El <xref:Microsoft.Office.Tools.Excel.ListObject> control puede eliminarse solo mediante la eliminación de las asignaciones y los objetos asignados desde el libro. Para obtener más información acerca de los controles, consulte [elementos Host y la información general sobre controles de Host](../vsto/host-items-and-host-controls-overview.md).  
  
-   BindingSource. Cuando se crea un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> asignando un elemento de esquema no repetitivo a la hoja de cálculo, un <xref:System.Windows.Forms.BindingSource> se crea y <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control se enlaza a la <xref:System.Windows.Forms.BindingSource>. Debe enlazar el <xref:System.Windows.Forms.BindingSource> a una instancia de origen de datos que coinciden con el esquema asignado al documento, como una instancia de tipo <xref:System.Data.DataSet> clase que se creó. Cree el enlace estableciendo el <xref:System.Windows.Forms.BindingSource.DataSource%2A> y <xref:System.Windows.Forms.BindingSource.DataMember%2A> propiedades, que se exponen en la **propiedades** ventana.  
  
    > [!NOTE]  
    >  El <xref:System.Windows.Forms.BindingSource> no se crea para <xref:Microsoft.Office.Tools.Excel.ListObject> objetos. Debe enlazar manualmente el <xref:Microsoft.Office.Tools.Excel.ListObject> al origen de datos estableciendo el <xref:System.Windows.Forms.BindingSource.DataSource%2A> y <xref:System.Windows.Forms.BindingSource.DataMember%2A> propiedades en el **propiedades** ventana.  
  
### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>Office asigna esquemas y la ventana de orígenes de datos de Visual Studio  
 La funcionalidad de esquema asignado de Office y Visual Studio **orígenes de datos** ventana puede ayudarle a presentar datos en una hoja de cálculo de Excel para crear informes o editar. En ambos casos puede arrastrar elementos de datos a la hoja de cálculo de Excel. Ambos métodos crean controles que están enlazados a través de un <xref:System.Windows.Forms.BindingSource> a un origen de datos como un <xref:System.Data.DataSet> o un servicio Web.  
  
> [!NOTE]  
>  Al asignar un elemento de esquema repetitivo a una hoja de cálculo, Visual Studio crea un <xref:Microsoft.Office.Tools.Excel.ListObject>. El <xref:Microsoft.Office.Tools.Excel.ListObject> no se enlaza automáticamente a los datos mediante el <xref:System.Windows.Forms.BindingSource>. Debe enlazar manualmente el <xref:Microsoft.Office.Tools.Excel.ListObject> al origen de datos estableciendo el <xref:System.Windows.Forms.BindingSource.DataSource%2A> y <xref:System.Windows.Forms.BindingSource.DataMember%2A> propiedades en el **propiedades** ventana.  
  
 En la tabla siguiente muestra algunas de las diferencias entre los dos métodos.  
  
|Esquema XML|Ventana de orígenes de datos|  
|----------------|-------------------------|  
|Usa la interfaz de Office.|Usa **orígenes de datos** ventana de Visual Studio.|  
|Habilita las características integradas de Office para importar y exportar datos desde archivos XML.|Debe permitir la importación y funcionalidad de exportación mediante programación.|  
|Debe escribir código para rellenar los controles generados con datos.|Los controles agregados desde la **orígenes de datos** ventana tiene el código generado automáticamente para rellenarlos, junto con las cadenas de conexión necesaria cuando se usan servidores de base de datos.|  
  
## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>Comportamiento cuando se asocian esquemas a documentos de Word  
 Objetos de datos no se crean cuando se asocia un esquema a un documento de Word que se utiliza en un proyecto de Office de nivel de documento. Sin embargo, al asignar un elemento de esquema en el documento, se crean controles. El tipo de control depende de qué tipo de elemento de asignación; generan elementos de repetición <xref:Microsoft.Office.Tools.Word.XMLNodes> , elementos y controles de no repetitivo generar <xref:Microsoft.Office.Tools.Word.XMLNode> controles. Para obtener más información, consulte [XMLNodes (Control)](../vsto/xmlnodes-control.md) y [XMLNode (Control)](../vsto/xmlnode-control.md).  
  
## <a name="deployment-of-solutions-that-include-xml-schemas"></a>Implementación de soluciones que incluyen esquemas XML  
 Debe crear un instalador para implementar una solución que utiliza un esquema XML que se asigna a un documento. El instalador debe registrar el esquema en la biblioteca de esquemas en el equipo del usuario. Si no registra el esquema, la solución seguirá funcionando porque Word genera un esquema temporal basándose en los elementos que están en el documento cuando el usuario lo abre. Sin embargo, el usuario no podrá realizar la validación frente a o guardar el esquema que se usó para crear el proyecto. Para obtener más información acerca de los instaladores, vea [implementar aplicaciones, servicios y componentes](/visualstudio/deployment/deploying-applications-services-and-components).  
  
 También puede agregar código al proyecto para comprobar si el esquema está en la biblioteca y registrado. Si no es así, puede avisar al usuario.  
  
 [!code-vb[Trin_VstcoreDataWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstcoreDataWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs#1)]  
  
## <a name="see-also"></a>Vea también  
 [Cómo: asignar esquemas a documentos de Word en Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Cómo: Asignar esquemas a hojas de cálculo en Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  