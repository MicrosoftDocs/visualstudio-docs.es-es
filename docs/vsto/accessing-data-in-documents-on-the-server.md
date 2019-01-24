---
title: Acceder a los datos de documentos en el servidor
ms.date: 02/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], accessing on server
- data access [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9d815178e772e391eb19eb43b5870fbcd9dbdaa6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53858109"
---
# <a name="access-data-in-documents-on-the-server"></a>Acceder a los datos de documentos en el servidor
  Puede programar los datos en una personalización de nivel de documento sin tener que usar el modelo de objetos de Microsoft Office Word o Microsoft Office Excel. Esto significa que puede tener acceso a datos que se encuentra en un documento en un servidor que no tiene Word o Excel instalado. Por ejemplo, el código en un servidor (por ejemplo, en un [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] página) puede personalizar los datos en un documento y enviar el documento personalizado para un usuario final. Cuando el usuario final abre el documento, el código de enlace de datos en el ensamblado de solución enlaza los datos personalizados en el documento. Esto es posible porque los datos en el documento se separan de la interfaz de usuario. Para obtener más información, consulte [en caché los datos en las personalizaciones de nivel de documento](../vsto/cached-data-in-document-level-customizations.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="cache-data-for-use-on-a-server"></a>Almacenar en caché datos para su uso en un servidor
 Para almacenar en caché un objeto de datos en un documento, márquelo con el <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> de atributo en tiempo de diseño, o utilice el `StartCaching` método de un elemento host en tiempo de ejecución. Al almacenar en caché un objeto de datos en un documento, el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] serializa el objeto en una cadena XML que se almacena en el documento. Los objetos deben cumplir ciertos requisitos para ser elegible para almacenar en caché. Para obtener más información, consulte [almacenar en caché datos](../vsto/caching-data.md).

 El código del lado servidor puede manipular los objetos de datos en la caché de datos. Controles enlazados a datos almacenados en caché instancias se sincronizan con la interfaz de usuario para que los cambios del lado servidor que se realizan en los datos se muestran automáticamente cuando se abre el documento en el cliente.

## <a name="access-data-in-the-cache"></a>Acceder a los datos en la memoria caché
 Puede tener acceso a datos en la memoria caché de aplicaciones fuera de oficina, por ejemplo desde una aplicación de consola, una aplicación de Windows Forms o una página Web. La aplicación que tiene acceso a los datos en caché debe tener plena confianza; una aplicación Web que tenga la confianza parcial no puede insertar, recuperar o cambiar los datos que se almacena en caché en un documento de Office.

 La caché de datos es accesible a través de una jerarquía de colecciones que expone el <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> propiedad de la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase:

- El <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> propiedad devuelve un <xref:Microsoft.VisualStudio.Tools.Applications.CachedData>, que contiene todos los datos en caché en una personalización de nivel de documento.

- Cada <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> contiene uno o varios <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> objetos. Un <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> contiene todos los objetos de datos almacenados en caché que se definen dentro de una sola clase.

- Cada <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> contiene uno o varios <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> objetos. Un <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> representa un objeto de datos en caché única.

  El código siguiente muestra cómo obtener acceso a una cadena almacenada en caché en el `Sheet1` clase de un proyecto de libro de Excel. Este ejemplo forma parte de un ejemplo más extenso proporcionado para el <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> método.

  [!code-csharp[Trin_ServerDocument#12](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#12)]
  [!code-vb[Trin_ServerDocument#12](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#12)]

## <a name="modify-data-in-the-cache"></a>Modificar datos en la memoria caché
 Para modificar un objeto de datos en caché, normalmente hay que realizar los pasos siguientes:

1.  Deserializar la representación XML del objeto en caché en una nueva instancia del objeto. Puede obtener acceso a XML mediante el <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> propiedad de la <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> que representa el objeto de datos almacenados en caché.

2.  Realice los cambios en esta copia.

3.  Serializar el objeto modificado en la caché de datos mediante una de las siguientes opciones:

    -   Si desea serializar automáticamente los cambios, utilice el <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> método. Este método usa la **DiffGram** formato para serializar <xref:System.Data.DataSet>, <xref:System.Data.DataTable>y con el tipo de objetos de conjunto de datos en la caché de datos. El **DiffGram** formato garantiza que los cambios realizados en la caché de datos en un documento sin conexión se envían correctamente al servidor.

    -   Si desea realizar su propia serialización para los cambios realizados en datos almacenados en caché, puede escribir directamente en el <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> propiedad. Especifique el **DiffGram** formato si usa un <xref:System.Data.Common.DataAdapter> para actualizar una base de datos con los cambios realizados a los datos en un <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, o con el tipo de conjunto de datos. En caso contrario, el <xref:System.Data.Common.DataAdapter> actualizará la base de datos agregando nuevas filas en lugar de modificar las filas existentes.

### <a name="modify-data-without-deserializing-the-current-value"></a>Modificar los datos sin deserializar el valor actual
 En algunos casos, es posible que desea modificar el valor del objeto en caché sin deserializar primero el valor actual. Por ejemplo, puede hacerlo si va a cambiar el valor de un objeto que tiene un tipo simple, como una cadena o entero, o si se está inicializando en caché <xref:System.Data.DataSet> en un documento en un servidor. En estos casos, puede usar el <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> método sin deserializar primero el valor actual del objeto en caché.

 En el ejemplo de código siguiente se muestra cómo cambiar el valor de una cadena almacenada en caché en el `Sheet1` clase de un proyecto de libro de Excel. Este ejemplo forma parte de un ejemplo más extenso proporcionado para el <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> método.

 [!code-csharp[Trin_ServerDocument#11](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#11)]

### <a name="modify-null-values-in-the-data-cache"></a>Modificar valores null en la caché de datos
 La caché de datos no almacena los objetos que tienen el valor **null** cuando se guarda y cierra el documento. Esta limitación tiene varias consecuencias al modificar los datos almacenados en caché:

-   Si establece cualquier objeto en la caché de datos en el valor **null**, todos los objetos en la caché de datos se establecerá automáticamente en **null** cuando se abre el documento y se borrará la caché de datos completa cuando el se guarda y cierra el documento. Es decir, todos los objetos almacenados en caché se quitará de la caché de datos y el <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> colección estará vacía.

-   Si compila una solución con **null** objetos en la caché de datos y desean inicializar estos objetos mediante el uso de la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase antes de que el documento se abre por primera vez, debe asegurarse de que inicializar todos los objetos en la caché de datos. Si se inicializan solo algunos de los objetos, todos los objetos se establecerá en **null** cuando se abre el documento y se borrará la memoria caché de datos completo cuando se guarda y cierra el documento.

## <a name="access-typed-datasets-in-the-cache"></a>Acceso con el tipo de los conjuntos de datos en la memoria caché
 Si desea tener acceso a los datos en un dataset con tipo desde una solución de Office y desde una aplicación fuera de oficina, como una aplicación de Windows Forms o un [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] proyecto, debe definir el conjunto de datos con tipo en un ensamblado independiente que se hace referencia en ambos proyectos. Si agregar el conjunto de datos con tipo para cada proyecto mediante el **configuración origen de datos** asistente o el **Diseñador de Dataset**, .NET Framework tratará los conjuntos de datos con tipo en los dos proyectos como tipos diferentes . Para obtener más información sobre la creación de conjuntos de datos con tipo, consulte [crear y configurar los conjuntos de datos en Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Vea también

- [Acceder a los datos de documentos en el servidor](../vsto/accessing-data-in-documents-on-the-server.md)
- [Datos almacenados en caché en las personalizaciones de nivel de documento](../vsto/cached-data-in-document-level-customizations.md)