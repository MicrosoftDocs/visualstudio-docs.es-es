---
title: "Esquemas y datos XML en personalizaciones de nivel de documento"
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
  - "desarrollo de Office en Visual Studio, XML"
  - "esquemas [desarrollo de Office en Visual Studio]"
  - "XML [desarrollo de Office en Visual Studio], esquemas XML"
  - "esquemas XML [desarrollo de Office en Visual Studio]"
  - "esquemas XML [desarrollo de Office en Visual Studio], acerca de los datos y esquemas XML"
ms.assetid: 74bd5773-6cb0-44fb-9738-75e2f2c6e48d
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Esquemas y datos XML en personalizaciones de nivel de documento
  La información de**Importante** The establecida en este tema relacionada con Microsoft Word se presenta exclusivamente para el marcado y el uso de individuos y organizaciones que se encuentran fuera de los Estados Unidos y sus territorios o que estén utilizando, o desarrollando programas que se ejecutan en, productos de Microsoft Word que se autorizados por Microsoft antes de enero de 2010, cuando Microsoft quitó una implementación de la funcionalidad concreta relacionada con XML personalizado de Microsoft Word.  Puede que esta información relacionada con Microsoft Word no sea leída o utilizada por individuos u organizaciones residentes en los Estados Unidos o sus territorios que estén utilizando, o desarrollando programas que se ejecutan en, productos de Microsoft Word con licencia concedida por Microsoft después del 10 de enero de 2010; dichos productos no tendrán el mismo comportamiento que los productos con licencia anterior a esa fecha o comprados, y con licencia para su uso, fuera de los Estados Unidos.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Microsoft Office Excel y Microsoft Office Word ofrecen la posibilidad de asignar esquemas a los documentos.  Dicha característica puede simplificar la importación y exportación de datos XML dentro y fuera del documento.  
  
 Visual Studio expone elementos de esquema asignados en personalizaciones de nivel de documento como controles en el modelo de programación.  Para Excel, Visual Studio además admite el enlace de controles a los datos en bases de datos, servicios Web y objetos.  Para Word y Excel, Visual Studio agrega compatibilidad con los paneles de acciones, que se pueden usar con documentos asignados a esquemas para mejorar la experiencia del usuario final con las soluciones.  Para obtener más información, vea [Información general sobre paneles de acciones](../vsto/actions-pane-overview.md).  
  
> [!NOTE]  
>  No puede utilizar esquemas XML compuestos en las soluciones de Excel.  
  
## Objetos creados cuando se asocian esquemas a libros de Excel  
 Cuando se asocia un esquema a un libro, Visual Studio automáticamente crea varios objetos y los agrega a su proyecto.  Dichos objetos no se deben eliminar utilizando Visual Studio Tools, porque los administra Excel.  Para eliminarlos, quite los elementos asignados de la hoja de cálculo o desasocie el esquema mediante las herramientas de Excel.  
  
 Hay dos objetos principales:  
  
-   Esquema XML \(archivo XSD\).  Por cada esquema del libro, Visual Studio agrega un esquema al proyecto.  Este esquema aparece como un elemento de proyecto con extensión XSD en **Explorador de soluciones**.  
  
-   Una clase <xref:System.Data.DataSet> con tipo.  Esta clase se crea basándose en el esquema.  Esta clase de conjunto de datos es visible en **Vista de clases**.  
  
## Objetos creados cuando se asignan elementos de esquema a hojas de cálculo de Excel  
 Cuando se asigna un elemento de esquema del panel de tareas **Origen XML** a una hoja de cálculo, Visual Studio crea automáticamente varios objetos y los agrega al proyecto.  
  
-   Controles.  Por cada objeto asignado en el libro, en el modelo de programación se crea un control <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> \(para los elementos de esquema que no sean de repetición\) o un control  <xref:Microsoft.Office.Tools.Excel.ListObject> \(para los elementos de esquema de repetición\).  El control <xref:Microsoft.Office.Tools.Excel.ListObject> sólo se puede eliminar eliminando las asignaciones y los objetos asignados del libro.  Para obtener más información sobre controles, vea [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md).  
  
-   BindingSource.  Cuando se crea un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> asignando un elemento de esquema no repetitivo a la hoja de cálculo, se crea un <xref:System.Windows.Forms.BindingSource> y el control <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> se enlaza con el <xref:System.Windows.Forms.BindingSource>.  Debe enlazar <xref:System.Windows.Forms.BindingSource> a una instancia del origen de datos que coincida con el esquema asignado al documento, como por ejemplo una instancia de la clase <xref:System.Data.DataSet> que se ha creado.  Cree el enlace estableciendo las propiedades <xref:System.Windows.Forms.BindingSource.DataSource%2A> y <xref:System.Windows.Forms.BindingSource.DataMember%2A>, que aparecen en la ventana **Propiedades**.  
  
    > [!NOTE]  
    >  <xref:System.Windows.Forms.BindingSource> no se crea para objetos <xref:Microsoft.Office.Tools.Excel.ListObject>.  Debe enlazar manualmente <xref:Microsoft.Office.Tools.Excel.ListObject> con el origen de datos estableciendo las propiedades <xref:System.Windows.Forms.BindingSource.DataSource%2A> y <xref:System.Windows.Forms.BindingSource.DataMember%2A> en la ventana **Propiedades**.  
  
### Esquemas asignados de Office y la ventana Orígenes de datos de Visual Studio  
 Tanto la funcionalidad de esquema asignado de Office como la ventana **Orígenes de datos** de Visual Studio le pueden ayudar a presentar datos en una hoja de cálculo de Excel para crear informes o editar.  En ambos casos, puede arrastrar los elementos de datos en la hoja de cálculo de Excel.  Ambos métodos crean controles enlazados a través de <xref:System.Windows.Forms.BindingSource> a un origen de datos como <xref:System.Data.DataSet> o a un servicio Web.  
  
> [!NOTE]  
>  Cuando se asigna un elemento de esquema repetitivo a una hoja de cálculo, Visual Studio crea un objeto <xref:Microsoft.Office.Tools.Excel.ListObject>.  <xref:Microsoft.Office.Tools.Excel.ListObject> no se enlaza automáticamente con los datos a través del <xref:System.Windows.Forms.BindingSource>.  Debe enlazar manualmente <xref:Microsoft.Office.Tools.Excel.ListObject> con el origen de datos estableciendo las propiedades <xref:System.Windows.Forms.BindingSource.DataSource%2A> y <xref:System.Windows.Forms.BindingSource.DataMember%2A> en la ventana **Propiedades**.  
  
 En la siguiente tabla se muestran algunas de las diferencias entre ambos métodos.  
  
|Esquema XML|Ventana de orígenes de datos|  
|-----------------|----------------------------------|  
|Utiliza la interfaz de Office.|Utiliza la ventana **Orígenes de datos** de Visual Studio.|  
|Habilita las características integradas de Office para importar y exportar datos de los archivos XML.|Debe proporcionar funcionalidad de importación y exportación mediante programación.|  
|Debe escribir código para llenar de datos los controles generados.|Los controles agregados desde la ventana **Orígenes de datos** tienen código generado automáticamente para rellenarlos, junto con las cadenas de conexión necesarias cuando utiliza servidores de bases de datos.|  
  
## Comportamiento cuando se asocian esquemas a documentos de Word  
 Si se asocia un esquema a un documento de Word que se usa en un proyecto de Office de nivel de documento, no se crean objetos de datos.  Sin embargo, si asigna un elemento de esquema a su documento, se crean controles.  El tipo de control depende de qué tipo de elemento asigne; los elementos que se repiten generan controles <xref:Microsoft.Office.Tools.Word.XMLNodes> y los elementos que no se repiten generan controles <xref:Microsoft.Office.Tools.Word.XMLNode>.  Para obtener más información, vea [XMLNodes &#40;Control&#41;](../vsto/xmlnodes-control.md) y [XMLNode &#40;Control&#41;](../vsto/xmlnode-control.md).  
  
## Implementación de soluciones que incluyen esquemas XML  
 Debe crear un instalador para implementar una solución que utiliza un esquema XML asignado a un documento.  El instalador debe registrar el esquema en la biblioteca de esquemas del equipo del usuario.  La solución funcionará aunque no registre el esquema, porque Word genera un esquema temporal basándose en los elementos que están en el documento cuando el usuario lo abre.  Sin embargo, el usuario no podrá guardar el esquema que se ha utilizado para crear el proyecto ni realizar una validación con respecto al mismo.  Para obtener más información sobre los instaladores, vea [Implementar aplicaciones, servicios y componentes](../deployment/deploying-applications-services-and-components.md).  
  
 También puede agregar código al proyecto para comprobar si el esquema está en la biblioteca y si está registrado.  Si no lo está, puede advertir al usuario.  
  
 [!code-csharp[Trin_VstcoreDataWord#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataWord/CS/ThisDocument.cs#1)]
 [!code-vb[Trin_VstcoreDataWord#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataWord/VB/ThisDocument.vb#1)]  
  
## Vea también  
 [Cómo: Asignar esquemas a documentos de Word en Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Cómo: Asignar esquemas a hojas de cálculo en Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  