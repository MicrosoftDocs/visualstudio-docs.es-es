---
title: "C&#243;mo: Almacenar datos en la memoria cach&#233; para el uso sin conexi&#243;n o en un servidor"
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
  - "datos [desarrollo de Office en Visual Studio], almacenar en caché"
  - "almacenamiento de datos en caché [desarrollo de Office en Visual Studio], uso sin conexión"
  - "almacenamiento de datos en caché [desarrollo de Office en Visual Studio], uso de servidor"
  - "conjuntos de datos [desarrollo de Office en Visual Studio], almacenar en caché"
  - "aplicaciones de Office [desarrollo de Office en Visual Studio], datos"
  - "datos sin conexión [desarrollo de Office en Visual Studio]"
ms.assetid: 6246b187-9413-4336-821d-2259b1adec5a
caps.latest.revision: 49
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 48
---
# C&#243;mo: Almacenar datos en la memoria cach&#233; para el uso sin conexi&#243;n o en un servidor
  Puede marcar un elemento de datos para que se almacene en memoria caché en el documento y esté así disponible sin conexión.  De esta forma, también se podrán manipular los datos del documento con otro código cuando dicho documento se encuentre almacenado en un servidor.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Puede marcar un elemento de datos para que se almacene en memoria caché cuando dicho elemento se declara en su código o, si está utilizando un objeto <xref:System.Data.DataSet>, tiene que especificar la propiedad en la ventana **Propiedades**.  Si está almacenando en memoria caché un elemento de datos que no es <xref:System.Data.DataSet> ni <xref:System.Data.DataTable>, asegúrese de que cumple los criterios para almacenarse en memoria caché en el documento.  Para obtener más información, vea [Almacenar datos en caché](../vsto/caching-data.md).  
  
> [!NOTE]  
>  Los nombres de los conjuntos de datos creados mediante Visual Basic que están marcados como **Cached** y **WithEvents** \(incluidos los conjuntos de datos arrastrados desde la ventana **Orígenes de datos** o **Cuadro de herramientas** cuya propiedad **CacheInDocument** está establecida en **True**\) vienen precedidos por un carácter de subrayado en la memoria caché.  Por ejemplo, si crea un conjunto de datos y lo denomina Customers, el nombre de <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> será \_Customers en la memoria caché.  Si usa <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> para obtener acceso al elemento almacenado en memoria caché, deberá especificar \_Customers en lugar de Customers.  
  
### Para almacenar datos en memoria caché en el documento mediante código  
  
1.  Declare una propiedad o campo público para el elemento de datos como un miembro de una clase de elementos host en su proyecto, como la clase `ThisDocumen`t en un proyecto de Word o la clase `ThisWorkbook` en un proyecto Excel.  
  
2.  Aplique el atributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> al miembro para marcar el elemento de datos que se va a almacenar en la memoria caché del documento.  En el ejemplo siguiente se aplica este atributo a una declaración de campo para un <xref:System.Data.DataSet>.  
  
     [!code-csharp[Trin_VstcoreDataExcel#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#11)]  
  
3.  Agregue código para crear una instancia del elemento de datos y, si corresponde, cargarlo desde la base de datos.  
  
     El elemento de datos sólo se carga cuando se crea por primera vez; después de esto, la memoria caché se queda con el documento y es preciso escribir otro código para actualizarlo.  
  
### Para almacenar un conjunto de datos en la memoria caché del documento mediante la ventana Propiedades  
  
1.  Agregue el conjunto de datos al proyecto con las herramientas del diseñador de Visual Studio; por ejemplo, puede agregar un origen de datos al proyecto a través de la ventana **Orígenes de datos**.  
  
2.  Si aún no tiene ninguna, cree una instancia del conjunto de datos y selecciónela en el diseñador.  
  
3.  En la ventana **Propiedades**, establezca la propiedad **CacheInDocument** en **True**.  
  
     Para obtener más información, vea [Propiedades de los proyectos de Office](../vsto/properties-in-office-projects.md).  
  
4.  En la ventana **Propiedades**, establezca la propiedad **Modifiers** en **Public** \(el valor predeterminado es **Internal**\).  
  
## Vea también  
 [Almacenar datos en caché](../vsto/caching-data.md)   
 [Cómo: Almacenar en memoria caché un origen de datos de un documento de Office mediante programación](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [Cómo: Almacenar datos en caché en un documento protegido por contraseña](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Acceso a datos de documentos en el servidor](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Guardar datos](../data-tools/saving-data.md)  
  
  