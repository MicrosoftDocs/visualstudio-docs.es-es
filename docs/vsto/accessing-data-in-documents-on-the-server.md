---
title: Acceso a datos en documentos en el servidor
description: Obtenga información sobre cómo puede programar con los datos de una personalización de nivel de documento sin tener que usar el modelo de objetos de Microsoft Office Word o Microsoft Office Excel.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0df6aef3c83d66b84f569e85e953fde8a3f0e16c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826777"
---
# <a name="access-data-in-documents-on-the-server"></a>Acceso a datos en documentos en el servidor
  Puede programar con los datos de una personalización de nivel de documento sin tener que usar el modelo de objetos de Microsoft Office Word o Microsoft Office Excel. Esto significa que puede acceder a los datos contenidos en un documento en un servidor que no tenga instalado Word o Excel. Por ejemplo, el código de un servidor (por ejemplo, en una página) puede personalizar los datos de un documento y enviar el documento personalizado [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] a un usuario final. Cuando el usuario final abre el documento, el código de enlace de datos del ensamblado de la solución enlaza los datos personalizados al documento. Esto es posible porque los datos del documento están separados de la interfaz de usuario. Para obtener más información, vea [Datos almacenados en caché en personalizaciones de nivel de documento.](../vsto/cached-data-in-document-level-customizations.md)

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="cache-data-for-use-on-a-server"></a>Almacenar en caché datos para su uso en un servidor
 Para almacenar en caché un objeto de datos en un documento, mónquelo con el atributo en tiempo de diseño o use el método de un elemento <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> host en tiempo de `StartCaching` ejecución. Cuando se almacena en caché un objeto de datos en un documento, serializa el objeto en una [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] cadena XML que se almacena en el documento. Los objetos deben cumplir determinados requisitos para ser aptos para el almacenamiento en caché. Para obtener más información, vea Almacenar [en caché los datos](../vsto/caching-data.md).

 El código del lado servidor puede manipular cualquier objeto de datos de la caché de datos. Los controles enlazados a instancias de datos almacenadas en caché se sincronizan con la interfaz de usuario, de modo que los cambios del lado servidor que se realicen en los datos se muestren automáticamente cuando el documento se abre en el cliente.

## <a name="access-data-in-the-cache"></a>Acceso a los datos de la memoria caché
 Puede acceder a los datos de la memoria caché desde aplicaciones fuera de Office, por ejemplo, desde una aplicación de consola, una aplicación Windows Forms o una página web. La aplicación que tiene acceso a los datos almacenados en caché debe tener plena confianza; una aplicación web que tiene confianza parcial no puede insertar, recuperar o cambiar datos almacenados en caché en un documento de Office.

 La caché de datos es accesible a través de una jerarquía de colecciones expuestas por <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> la propiedad de la clase <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> :

- La propiedad devuelve , que contiene todos los datos almacenados en <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> caché en una personalización de nivel de documento.

- Cada <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> contiene uno o más objetos <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem>. contiene <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> todos los objetos de datos almacenados en caché que se definen dentro de una sola clase.

- Cada <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> contiene uno o más objetos <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>. representa <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> un único objeto de datos almacenado en caché.

  En el ejemplo de código siguiente se muestra cómo acceder a una cadena almacenada en caché en la `Sheet1` clase de un proyecto de libro de Excel. Este ejemplo forma parte de un ejemplo mayor que se proporciona para el <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> método .

  :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs" id="Snippet12":::
  :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb" id="Snippet12":::

## <a name="modify-data-in-the-cache"></a>Modificación de datos en la memoria caché
 Para modificar un objeto de datos almacenado en caché, normalmente se realizan los pasos siguientes:

1. Deserialice la representación XML del objeto almacenado en caché en una nueva instancia del objeto . Puede acceder al XML mediante la propiedad de que <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> representa el objeto de datos almacenado en <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> caché.

2. Realice los cambios en esta copia.

3. Vuelva a serializar el objeto cambiado en la caché de datos mediante una de las siguientes opciones:

    - Si desea serializar automáticamente los cambios, use el <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> método . Este método usa el formato **DiffGram** para serializar objetos de conjunto de datos con tipo , y <xref:System.Data.DataSet> en la caché de <xref:System.Data.DataTable> datos. El **formato DiffGram** garantiza que los cambios en la caché de datos de un documento sin conexión se envían correctamente al servidor.

    - Si desea realizar su propia serialización para los cambios en los datos almacenados en caché, puede escribir directamente en la <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> propiedad . Especifique el **formato DiffGram** si usa para actualizar una base de datos con los cambios realizados en los datos de un conjunto de datos con tipo <xref:System.Data.Common.DataAdapter> , o <xref:System.Data.DataSet> <xref:System.Data.DataTable> . De lo contrario, <xref:System.Data.Common.DataAdapter> actualizará la base de datos agregando nuevas filas en lugar de modificar las filas existentes.

### <a name="modify-data-without-deserializing-the-current-value"></a>Modificar datos sin deserializar el valor actual
 En algunos casos, es posible que desee modificar el valor del objeto almacenado en caché sin deserializar primero el valor actual. Por ejemplo, puede hacerlo si va a cambiar el valor de un objeto que tiene un tipo simple, como una cadena o un entero, o si va a inicializar un objeto almacenado en caché en un documento en un <xref:System.Data.DataSet> servidor. En estos casos, puede usar el <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> método sin deserializar primero el valor actual del objeto almacenado en caché.

 En el ejemplo de código siguiente se muestra cómo cambiar el valor de una cadena almacenada en caché en la `Sheet1` clase de un proyecto de libro de Excel. Este ejemplo forma parte de un ejemplo mayor que se proporciona para el <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> método .

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs" id="Snippet11":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb" id="Snippet11":::

### <a name="modify-null-values-in-the-data-cache"></a>Modificación de valores NULL en la caché de datos
 La memoria caché de datos no almacena objetos que tengan el valor **NULL** cuando el documento se guarda y se cierra. Esta limitación tiene varias consecuencias al modificar los datos almacenados en caché:

- Si establece cualquier objeto de la caché de datos en el valor **null**, todos los objetos de la caché de datos se establecerán automáticamente en **NULL** cuando se abra el documento y se borrará toda la caché de datos cuando se guarde y se cierre el documento. Es decir, todos los objetos almacenados en caché se quitarán de la caché de datos y la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> colección estará vacía.

- Si compila una solución con objetos **NULL** en la caché de datos y desea inicializar estos objetos mediante la clase antes de que el documento se abra por primera vez, debe asegurarse de inicializar todos los objetos de la caché de <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> datos. Si inicializa solo algunos de los objetos, todos los objetos se establecerán en **NULL** cuando se abra el documento y se borrará toda la caché de datos cuando se guarde y se cierre el documento.

## <a name="access-typed-datasets-in-the-cache"></a>Acceso a conjuntos de datos con tipo en la memoria caché
 Si desea acceder a los datos de un conjunto de datos con tipo desde una solución de Office y desde una aplicación fuera de Office, como una aplicación de Windows Forms o un proyecto, debe definir el conjunto de datos con tipo en un ensamblado independiente al que se hace referencia en ambos [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] proyectos. Si agrega el conjunto de datos con  tipo a cada proyecto mediante el Asistente para configuración de origen de datos o el Diseñador de DataSet **,** el .NET Framework tratará los conjuntos de datos con tipo en los dos proyectos como tipos diferentes. Para obtener más información sobre cómo crear conjuntos de datos con tipo, vea [Crear y configurar conjuntos de](../data-tools/create-and-configure-datasets-in-visual-studio.md)datos en Visual Studio .

## <a name="see-also"></a>Consulte también

- [Acceso a datos en documentos en el servidor](../vsto/accessing-data-in-documents-on-the-server.md)
- [Datos almacenados en caché en personalizaciones de nivel de documento](../vsto/cached-data-in-document-level-customizations.md)