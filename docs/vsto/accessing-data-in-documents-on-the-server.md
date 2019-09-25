---
title: Acceder a los datos de documentos en el servidor
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], accessing on server
- data access [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ab033120c0913bbae33458c5a2d0b53972364581
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255766"
---
# <a name="access-data-in-documents-on-the-server"></a>Acceder a los datos de documentos en el servidor
  Puede programar con los datos de una personalización de nivel de documento sin tener que usar el modelo de objetos de Microsoft Office Word o Microsoft Office Excel. Esto significa que puede tener acceso a los datos contenidos en un documento en un servidor que no tiene instalado Word o Excel. Por ejemplo, el código de un servidor (por ejemplo, en [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] una página) puede personalizar los datos de un documento y enviar el documento personalizado a un usuario final. Cuando el usuario final abre el documento, el código de enlace de datos en el ensamblado de la solución enlaza los datos personalizados al documento. Esto es posible porque los datos del documento se separan de la interfaz de usuario. Para obtener más información, vea [datos almacenados en caché en personalizaciones de nivel de documento](../vsto/cached-data-in-document-level-customizations.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="cache-data-for-use-on-a-server"></a>Almacenar datos en caché para su uso en un servidor
 Para almacenar en caché un objeto de datos en un documento, márquelo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> con el atributo en tiempo de diseño o `StartCaching` use el método de un elemento host en tiempo de ejecución. Al almacenar en memoria caché un objeto de datos de un [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] documento, serializa el objeto en una cadena XML que se almacena en el documento. Los objetos deben cumplir ciertos requisitos para ser válidos para el almacenamiento en caché. Para obtener más información, vea [almacenar datos en caché](../vsto/caching-data.md).

 El código del lado servidor puede manipular cualquier objeto de datos en la memoria caché de datos. Los controles que están enlazados a las instancias de datos almacenadas en caché se sincronizan con la interfaz de usuario, de modo que los cambios del servidor que se realicen en los datos se muestren automáticamente cuando se abra el documento en el cliente.

## <a name="access-data-in-the-cache"></a>Acceder a los datos en la memoria caché
 Puede tener acceso a los datos de la memoria caché desde aplicaciones fuera de Office, por ejemplo, desde una aplicación de consola, una aplicación Windows Forms o una página web. La aplicación que tiene acceso a los datos almacenados en caché debe tener plena confianza; una aplicación web que tiene confianza parcial no puede insertar, recuperar o cambiar datos almacenados en caché en un documento de Office.

 La memoria caché de datos es accesible a través de una jerarquía de colecciones que <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> se expone mediante <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> la propiedad de la clase:

- La <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> propiedad<xref:Microsoft.VisualStudio.Tools.Applications.CachedData>devuelve, que contiene todos los datos almacenados en caché en una personalización de nivel de documento.

- Cada <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> contiene uno o varios <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> objetos. Un <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> objeto contiene todos los objetos de datos almacenados en memoria caché que se definen dentro de una sola clase.

- Cada <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> contiene uno o varios <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> objetos. <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> Representa un único objeto de datos almacenado en memoria caché.

  En el ejemplo de código siguiente se muestra cómo obtener acceso a una cadena `Sheet1` almacenada en caché en la clase de un proyecto de libro de Excel. Este ejemplo forma parte de un ejemplo más grande que se proporciona para <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> el método.

  [!code-csharp[Trin_ServerDocument#12](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#12)]
  [!code-vb[Trin_ServerDocument#12](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#12)]

## <a name="modify-data-in-the-cache"></a>Modificar datos en la memoria caché
 Para modificar un objeto de datos almacenado en memoria caché, normalmente se realizan los pasos siguientes:

1. Deserialice la representación XML del objeto almacenado en caché en una nueva instancia del objeto. Puede tener acceso al XML mediante la <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> propiedad <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> de que representa el objeto de datos almacenado en memoria caché.

2. Realice los cambios en esta copia.

3. Vuelva a serializar el objeto cambiado en la memoria caché de datos mediante una de las siguientes opciones:

    - Si desea serializar los cambios automáticamente, use el <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> método. Este método usa el formato **DiffGram** para serializar <xref:System.Data.DataSet>los <xref:System.Data.DataTable>objetos de conjunto de datos con tipo, y en la memoria caché de datos. El formato **DiffGram** garantiza que los cambios en la memoria caché de datos en un documento sin conexión se envían correctamente al servidor.

    - Si desea realizar su propia serialización para los cambios en los datos en caché, puede escribir directamente en la <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> propiedad. Especifique el formato **DiffGram** si utiliza <xref:System.Data.Common.DataAdapter> para actualizar una base de datos con los cambios realizados en los datos de un objeto, <xref:System.Data.DataTable>o un <xref:System.Data.DataSet>conjunto de datos con tipo. De lo contrario <xref:System.Data.Common.DataAdapter> , actualizará la base de datos agregando nuevas filas en lugar de modificar las filas existentes.

### <a name="modify-data-without-deserializing-the-current-value"></a>Modificar datos sin deserializar el valor actual
 En algunos casos, es posible que desee modificar el valor del objeto almacenado en caché sin deserializar primero el valor actual. Por ejemplo, puede hacerlo si va a cambiar el valor de un objeto que tiene un tipo simple, como una cadena o un entero, o si está inicializando un almacenado <xref:System.Data.DataSet> en caché en un documento de un servidor. En estos casos, puede utilizar el <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> método sin deserializar primero el valor actual del objeto almacenado en caché.

 En el ejemplo de código siguiente se muestra cómo cambiar el valor de una cadena almacenada `Sheet1` en caché en la clase de un proyecto de libro de Excel. Este ejemplo forma parte de un ejemplo más grande que se proporciona para <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> el método.

 [!code-csharp[Trin_ServerDocument#11](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#11)]

### <a name="modify-null-values-in-the-data-cache"></a>Modificar valores NULL en la memoria caché de datos
 La memoria caché de datos no almacena los objetos que tienen el valor **null** cuando se guarda y se cierra el documento. Esta limitación tiene varias consecuencias cuando se modifican los datos almacenados en caché:

- Si establece un objeto en la memoria caché de datos en el valor **null**, todos los objetos de la memoria caché de datos se establecerán automáticamente en **null** cuando se abra el documento y se borrará toda la memoria caché de datos cuando se guarde y cierre el documento. Es decir, todos los objetos almacenados en memoria caché se quitarán de la memoria caché de datos <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> y la colección estará vacía.

- Si compila una solución con objetos **null** en la memoria caché de datos y desea inicializar estos objetos mediante la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase antes de que se abra el documento por primera vez, debe asegurarse de que inicializa todos los objetos en la memoria caché de datos. Si solo inicializa algunos de los objetos, todos los objetos se establecerán en **null** cuando se abra el documento y se borrará toda la memoria caché de datos cuando se guarde y cierre el documento.

## <a name="access-typed-datasets-in-the-cache"></a>Obtener acceso a los conjuntos de DataSet con tipo en la memoria caché
 Si desea tener acceso a los datos de un conjunto de datos con tipo desde una solución de Office y desde una aplicación fuera de Office, como una aplicación Windows Forms o [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] un proyecto, debe definir el conjunto de datos con tipo en un ensamblado independiente al que se hace referencia en ambos. proyecto. Si agrega el conjunto de datos con tipo a cada proyecto mediante el Asistente para la **configuración de orígenes de datos** o el **Diseñador de DataSet**, el .NET Framework tratará los conjuntos de datos con tipo en los dos proyectos como tipos diferentes. Para obtener más información sobre cómo crear conjuntos de datos con tipo, vea [crear y configurar conjuntos de datos en Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Vea también

- [Acceder a los datos de documentos en el servidor](../vsto/accessing-data-in-documents-on-the-server.md)
- [Datos almacenados en caché en personalizaciones de nivel de documento](../vsto/cached-data-in-document-level-customizations.md)