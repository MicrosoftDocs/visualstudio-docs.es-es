---
title: Datos de caché
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], about caching data
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c6e0f6d7fcf9920ddb8861712b7c5f8bf04506fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62939420"
---
# <a name="cache-data"></a>Datos de caché
  Puede almacenar en caché objetos de datos en una personalización de nivel de documento para que se pueda tener acceso a los datos sin conexión o sin abrir Microsoft Office Word o Microsoft Office Excel. Para almacenar en caché un objeto, el objeto debe tener un tipo de datos que cumpla determinados requisitos. Muchos tipos de datos comunes en el .NET Framework cumplen estos requisitos, incluidos <xref:System.String> , <xref:System.Data.DataSet> y <xref:System.Data.DataTable> .

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Hay dos maneras de agregar un objeto a la memoria caché de datos:

- Para agregar un objeto a la memoria caché de datos al compilar la solución, aplique el <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atributo a la declaración del objeto. Para obtener más información, consulte [Cómo: almacenar datos en caché para su uso sin conexión o en un servidor](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Para agregar mediante programación un objeto a la memoria caché de datos en tiempo de ejecución, use el `StartCaching` método de un elemento host, como las `ThisDocument` `ThisWorkbook` clases o. Para obtener más información, consulte [Cómo: almacenar en caché un origen de datos en un documento de Office mediante programación](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).

  Después de agregar un objeto a la memoria caché de datos, puede obtener acceso y modificar los datos almacenados en caché sin iniciar Word o Excel. Para obtener más información, vea [obtener acceso a los datos de documentos en el servidor](../vsto/accessing-data-in-documents-on-the-server.md).

## <a name="requirements-for-data-objects-to-be-cached"></a>Requisitos para almacenar en caché los objetos de datos
 Para almacenar en caché un objeto de datos en la solución, el objeto debe cumplir estos requisitos:

- Ser un campo público de lectura/escritura o una propiedad de un elemento host, como `ThisDocument` las `ThisWorkbook` clases o.

- No ser un indexador ni otra propiedad parametrizada.

  Además, el objeto de datos debe ser serializable por la <xref:System.Xml.Serialization.XmlSerializer> clase, lo que significa que el tipo del objeto debe tener estas características:

- Ser un tipo público.

- Tener un constructor público sin parámetros.

- No ejecutar código que requiere privilegios de seguridad adicionales.

- Exponer solo propiedades públicas de lectura/escritura (se omitirán otras propiedades).

- No exponga matrices multidimensionales (se aceptan matrices anidadas).

- No se devuelven interfaces de propiedades y campos.

- No implemente <xref:System.Collections.IDictionary> si es una colección.

  Al almacenar en memoria caché un objeto de datos, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] serializa el objeto en una cadena XML que se almacena en un *elemento XML personalizado* en el documento. Para obtener más información, vea [información general sobre los elementos XML personalizados](../vsto/custom-xml-parts-overview.md).

## <a name="cached-data-size-limits"></a>Límites de tamaño de datos en caché
 Hay algunos límites en la cantidad total de datos que puede Agregar a la memoria caché de datos en un documento y en el tamaño de cualquier objeto individual en la memoria caché de datos. Si supera estos límites, la aplicación podría cerrarse de forma inesperada cuando se guarden los datos en la memoria caché de datos.

 Para evitar estos límites, siga estas instrucciones:

- No agregue ningún objeto mayor de 10 MB a la memoria caché de datos.

- No agregue más de 100 MB de datos totales a la memoria caché de datos en un solo documento.

  Estos son valores aproximados. Los límites exactos dependen de varios factores, como la RAM disponible y el número de procesos en ejecución.

## <a name="control-the-behavior-of-cached-objects"></a>Controlar el comportamiento de los objetos almacenados en caché
 Para obtener más control sobre el comportamiento de un objeto almacenado en memoria caché, puede implementar la <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interfaz en el tipo del objeto almacenado en caché. Por ejemplo, puede implementar esta interfaz si desea controlar cómo se notifica al usuario cuando se ha cambiado el objeto. Para ver ejemplos de código que muestran cómo implementar <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> , vea la `ControlCollection` clase en el ejemplo de controles dinámicos de Excel y el ejemplo de controles dinámicos de Word en [ejemplos y tutoriales de desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md).

## <a name="persist-changes-to-cached-data-in-password-protected-documents"></a>Conservar los cambios en los datos almacenados en caché en documentos protegidos mediante contraseña
 Si almacena en caché los objetos de datos de un documento que está protegido con una contraseña, no se guardan los cambios realizados en los datos almacenados en caché. Puede guardar los cambios en los datos almacenados en caché invalidando dos métodos. Invalide estos métodos para quitar temporalmente la protección cuando se guarda el documento y, a continuación, vuelva a aplicar la protección una vez completada la operación de guardar.

 Para obtener más información, consulte [Cómo: almacenar datos en caché en un documento protegido mediante contraseña](../vsto/how-to-cache-data-in-a-password-protected-document.md).

## <a name="prevent-data-loss-when-adding-null-values-to-the-data-cache"></a>Evitar la pérdida de datos al agregar valores NULL a la memoria caché de datos
 Al agregar objetos a la memoria caché de datos, todos los objetos almacenados en caché se deben inicializar en un valor distinto de**null** antes de guardar y cerrar el documento. Si algún objeto almacenado en memoria caché tiene un valor **null** cuando el documento se guarda y se cierra, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] quitará automáticamente todos los objetos almacenados en caché de la memoria caché de datos.

 Si agrega un objeto con un valor **null** a la memoria caché de datos utilizando el <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atributo en tiempo de diseño, puede usar la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase para inicializar los objetos de datos almacenados en memoria caché antes de que se abra el documento. Esto resulta útil si desea inicializar los datos almacenados en caché en un servidor sin Word o Excel instalado, antes de que un usuario final Abra el documento. Para obtener más información, vea [obtener acceso a los datos de documentos en el servidor](../vsto/accessing-data-in-documents-on-the-server.md).

## <a name="see-also"></a>Consulte también
- [Cómo: almacenar datos en caché para su uso sin conexión o en un servidor](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Cómo: almacenar en caché un origen de datos en un documento de Office mediante programación](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [Cómo: almacenar datos en caché en un documento protegido mediante contraseña](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Tutorial: crear una relación maestra-detalle mediante un conjunto de información almacenado en caché](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)
