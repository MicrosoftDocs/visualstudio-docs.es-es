---
title: "Acceso a datos de documentos en el servidor"
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
  - "datos [desarrollo de Office en Visual Studio], acceso en el servidor"
  - "acceso a datos [desarrollo de Office en Visual Studio]"
ms.assetid: 14a42e96-ed2f-48a1-a0c0-e19f9eba4956
caps.latest.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 31
---
# Acceso a datos de documentos en el servidor
  Se puede programar basándose en los datos de un documento sin tener que utilizar el modelo de objetos de Microsoft Office Word o Microsoft Office Excel.  Esto significa que puede tener acceso a los datos contenidos en un documento en un servidor que no tenga Word ni Excel instalados.  Por ejemplo, el código de un servidor \(como en una página [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]\) puede personalizar los datos de un documento y enviar el documento personalizado a un usuario final.  Cuando el usuario final abre el documento, el código de enlace de datos del ensamblado de la solución enlaza los datos personalizados del documento.  Esto es posible porque los datos del documento están separados de la interfaz de usuario.  Para obtener más información, vea [Datos almacenados en caché en las personalizaciones de nivel de documento](../vsto/cached-data-in-document-level-customizations.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Almacenar en memoria caché los datos para su uso en un servidor  
 Para almacenar en memoria caché un objeto de datos de un documento, márquelo en tiempo de diseño con el atributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> o utilice en tiempo de ejecución el método `StartCaching` de un elemento host.  Cuando se almacena en la memoria caché un objeto de datos de un documento, el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] serializa el objeto en una cadena XML que se almacena en el documento.  Los objetos deben cumplir determinados requisitos para que puedan almacenarse en memoria caché.  Para obtener más información, vea [Almacenar datos en caché](../vsto/caching-data.md).  
  
 El código del servidor puede manipular cualquier objeto de datos en la caché de datos.  Los controles que están enlazados a instancias de datos almacenadas en memoria caché se sincronizan con la interfaz de usuario, de manera que los cambios del lado del servidor realizados en los datos se mostrarán automáticamente cuando el documento se abra en el cliente.  
  
## Tener acceso a los datos de la memoria caché  
 Es posible tener acceso a los datos contenidos en la memoria caché de aplicaciones ajenas a Office, por ejemplo, desde una aplicación de consola, una aplicación de formularios Windows Forms o una página Web.  La aplicación que tiene acceso a los datos almacenados en memoria caché debe tener plena confianza; una aplicación Web que sólo tenga confianza parcial no puede insertar, recuperar ni cambiar los datos almacenados en la memoria caché de un documento de Office.  
  
 Se puede obtener acceso a la caché de datos a través de una jerarquía de colecciones ofrecida por la propiedad <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> de la clase <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>:  
  
-   La propiedad <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> devuelve <xref:Microsoft.VisualStudio.Tools.Applications.CachedData>, que contiene todos los datos almacenados en memoria caché en una personalización de nivel de documento.  
  
-   Cada <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> contiene uno o más objetos <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem>.  <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> contiene todos los objetos de datos almacenados en memoria caché que se definen dentro de una clase única.  
  
-   Cada <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> contiene uno o más objetos <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>.  <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> representa un único objeto de datos almacenado en la memoria caché.  
  
 En el ejemplo de código siguiente se muestra cómo tener acceso a una cadena almacenada en memoria caché en la clase `Sheet1` de un proyecto de libro de Excel.  Este ejemplo forma parte de un ejemplo más extenso proporcionado para el método <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A>.  
  
 [!code-csharp[Trin_ServerDocument#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ServerDocument/CS/Form1.cs#12)]
 [!code-vb[Trin_ServerDocument#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ServerDocument/VB/Form1.vb#12)]  
  
## Modificar datos en la caché  
 Para modificar un objeto de datos almacenado en la memoria caché, normalmente se siguen estos pasos:  
  
1.  Deserialice la representación XML del objeto en caché en una nueva instancia del objeto.  Puede tener acceso al código XML utilizando la propiedad <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> de <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> que representa el objeto de datos almacenado en memoria caché.  
  
2.  Realice los cambios en esta copia.  
  
3.  Serialice de nuevo el objeto modificado en la caché de datos utilizando una de las opciones siguientes:  
  
    -   Si desea serializar automáticamente los cambios, utilice el método <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A>.  Este método utiliza el formato **DiffGram** para serializar objetos de <xref:System.Data.DataSet>, de <xref:System.Data.DataTable> y de conjuntos de datos con tipo en la caché de datos.  El formato **DiffGram** garantiza que los cambios en la caché de datos de un documento sin conexión se envían correctamente al servidor.  
  
    -   Si desea realizar su propia serialización para llevar a cabo cambios en los datos almacenados en memoria caché, puede escribir directamente en la propiedad <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A>.  Especifique el formato **DiffGram** si utiliza un <xref:System.Data.Common.DataAdapter> para actualizar una base de datos con los cambios efectuados en datos en un <xref:System.Data.DataSet>, <xref:System.Data.DataTable> o un conjunto de datos con tipo.  De lo contrario, el <xref:System.Data.Common.DataAdapter> actualizará la base de datos agregando nuevas filas en lugar de modificar las filas existentes.  
  
### Modificar datos sin deserializar el valor actual  
 En algunos casos, puede ser conveniente modificar el valor del objeto en caché sin deserializar antes su valor actual.  Por ejemplo, puede hacerlo para modificar el valor de un objeto que tiene un tipo simple, como una cadena o un entero, o inicializar un <xref:System.Data.DataSet> almacenado en memoria caché en un documento de un servidor.  En estos casos, puede utilizar el método <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> sin deserializar primero el valor actual del objeto en caché.  
  
 En el ejemplo de código siguiente se muestra cómo cambiar el valor de una cadena almacenada en memoria caché en la clase `Sheet1` de un proyecto de libro de Excel.  Este ejemplo forma parte de un ejemplo más extenso proporcionado para el método <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A>.  
  
 [!code-csharp[Trin_ServerDocument#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ServerDocument/CS/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ServerDocument/VB/Form1.vb#11)]  
  
### Modificar los valores Null en la caché de datos  
 La caché de datos no almacena objetos cuyo valor es **null** al guardar y cerrar el documento.  Esta limitación tiene varias consecuencias al modificar los datos almacenados en memoria caché:  
  
-   Si establece cualquier objeto de la caché de datos en el valor **null**, todos los objetos de la caché de datos se establecerán automáticamente en **null** al abrir el documento, y la caché de datos completa se borrará al guardar y cerrar el documento.  Es decir, todos los objetos en caché se quitarán de la caché de datos y la colección <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> quedará vacía.  
  
-   Si compila una solución con objetos **null** en la caché de datos y desea inicializar estos objetos utilizando la clase <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> antes de abrir el documento por primera vez, debe asegurarse de inicializar todos los objetos en la caché de datos.  Si sólo inicializa algunos de ellos, todos se establecerán en **null** al abrir el documento, y la caché de datos completa se borrará al guardar y cerrar el documento.  
  
## Tener acceso a conjuntos de datos con tipo en la caché  
 Si desea obtener acceso a los datos de un conjunto de datos con tipo de una solución de Office y de una aplicación fuera de Office, como una aplicación de Windows Forms o un proyecto de [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)], deberá definir dicho conjunto de datos en un ensamblado independiente al que se haga referencia en ambos proyectos.  Si agrega el conjunto de datos con tipo a cada proyecto mediante el **Asistente para la configuración de orígenes de datos** o el **Diseñador de DataSet**, .NET Framework tratará los conjuntos de datos con tipo que aparecen en los dos proyectos como tipos diferentes.  Para obtener más información sobre cómo crear conjuntos de datos con tipo, vea [Cómo: Crear un conjunto de datos con tipo](../Topic/Creating%20and%20configuring%20datasets%20in%20Visual%20Studio.md).  
  
## Vea también  
 [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Datos almacenados en caché en las personalizaciones de nivel de documento](../vsto/cached-data-in-document-level-customizations.md)  
  
  