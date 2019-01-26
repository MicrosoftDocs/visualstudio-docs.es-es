---
title: Almacenar datos en caché
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
ms.openlocfilehash: 4bdd98dfc9437fb9090ce813f7d8458747b20196
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866745"
---
# <a name="cache-data"></a>Almacenar datos en caché
  Puede almacenar en caché objetos de datos en una personalización de nivel de documento para que se tiene acceso a los datos sin conexión o sin tener que abrir Microsoft Office Word o Microsoft Office Excel. Para almacenar en caché un objeto, el objeto debe tener un tipo de datos que cumple determinados requisitos. Muchos tipos de datos comunes en .NET Framework cumplen estos requisitos, incluyendo <xref:System.String>, <xref:System.Data.DataSet>, y <xref:System.Data.DataTable>.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Hay dos maneras de agregar un objeto a la caché de datos:  
  
- Para agregar un objeto a la caché de datos cuando se compila la solución, aplique el <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atributo a la declaración del objeto. Para obtener más información, vea [Cómo: Almacenar en caché datos para su uso sin conexión o en un servidor](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
- Para agregar mediante programación un objeto a la caché de datos en tiempo de ejecución, use el `StartCaching` elemento de método de un host, como el `ThisDocument` o `ThisWorkbook` clases. Para obtener más información, vea [Cómo: Almacenar en caché mediante programación un origen de datos en un documento de Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).  
  
  Después de agregar un objeto a la caché de datos, puede acceder y modificar los datos en caché sin iniciar Word o Excel. Para obtener más información, consulte [tener acceso a datos de documentos en el servidor](../vsto/accessing-data-in-documents-on-the-server.md).  
  
## <a name="requirements-for-data-objects-to-be-cached"></a>Requisitos para los objetos de datos en la memoria caché  
 Para almacenar en caché un objeto de datos de la solución, el objeto debe cumplir estos requisitos:  
  
- Ser un campo público de lectura/escritura o una propiedad de un elemento host, como el `ThisDocument` o `ThisWorkbook` clases.  
  
- No ser un indizador ni otra propiedad parametrizada.  
  
  Además, el objeto de datos debe ser serializable por la <xref:System.Xml.Serialization.XmlSerializer> (clase), lo que significa que el tipo del objeto debe tener estas características:  
  
- Ser un tipo público.  
  
- Tener un constructor público sin parámetros.  
  
- No ejecutar código que requiere privilegios de seguridad adicionales.  
  
- Exponer solo lectura y escritura propiedades públicas (se omitirán otras propiedades).  
  
- No exponga matrices multidimensionales (se aceptan matrices anidadas).  
  
- No debe devolver interfaces de propiedades y campos.  
  
- No implemente <xref:System.Collections.IDictionary> si es una colección.  
  
  Al almacenar en caché un objeto de datos, el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] serializa el objeto en una cadena XML que se almacena en un *elemento XML personalizado* en el documento. Para obtener más información, consulte [información general de elementos XML personalizados](../vsto/custom-xml-parts-overview.md).  
  
## <a name="cached-data-size-limits"></a>Límites de tamaño de datos almacenados en caché  
 Hay algunos límites en la cantidad total de datos que se puede agregar a la caché de datos en un documento y el tamaño de cualquier objeto individual de la caché de datos. Si supera estos límites, la aplicación podría cerrarse inesperadamente cuando los datos se guardan en la caché de datos.  
  
 Para evitar estos límites, siga estas directrices:  
  
- No agregue ningún objeto mayor que 10 MB a la caché de datos.  
  
- No agregue más de 100 MB de datos total a la caché de datos en un único documento.  
  
  Estos valores son aproximados. Los límites exactos dependen de varios factores, como la memoria RAM disponible y el número de procesos en ejecución.  
  
## <a name="control-the-behavior-of-cached-objects"></a>Controlar el comportamiento de los objetos en caché  
 Para obtener más control sobre el comportamiento de un objeto almacenado en caché, puede implementar el <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interfaz en el tipo de objeto en caché. Por ejemplo, puede implementar esta interfaz si desea controlar cómo se notifica al usuario cuando el objeto se ha cambiado. Para obtener ejemplos de código que muestran cómo implementar <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>, consulte el `ControlCollection` clase en el ejemplo de controles dinámicos de Excel y Word de ejemplo de controles dinámicos en [tutoriales y ejemplos de desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
## <a name="persist-changes-to-cached-data-in-password-protected-documents"></a>Conservar los cambios a los datos almacenados en caché de documentos protegidos con contraseña  
 Si almacena en caché objetos de datos en un documento que está protegido con una contraseña, no se guardan los cambios realizados en los datos en caché. Puede guardar los cambios a los datos almacenados en caché mediante el reemplazo de dos métodos. Invalidar estos métodos para quitar temporalmente la protección cuando se guarda el documento y, a continuación, volver a aplicar la protección después de guardar completada la operación.  
  
 Para obtener más información, vea [Cómo: Almacenar en caché datos en un documento protegido por contraseña](../vsto/how-to-cache-data-in-a-password-protected-document.md).  
  
## <a name="prevent-data-loss-when-adding-null-values-to-the-data-cache"></a>Evitar la pérdida de datos al agregar los valores null a la caché de datos  
 Cuando se agregan objetos a la caché de datos, todos los objetos almacenados en caché se deben inicializar para que no es**null** valor antes de que se guarda y cierra el documento. Si tiene cualquier objeto almacenado en caché un **null** valor cuando el documento se guarda y cierra, la [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] quitará automáticamente todos los objetos almacenados en caché de la caché de datos.  
  
 Si agrega un objeto con un **null** valor a la caché de datos mediante el uso de la <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atributos en tiempo de diseño, puede usar el <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase para inicializar los datos en caché los objetos antes de que se abre el documento. Esto es útil si desea inicializar los datos en caché en un servidor sin Word o Excel instalada antes de que el documento está abierto en un usuario final. Para obtener más información, consulte [tener acceso a datos de documentos en el servidor](../vsto/accessing-data-in-documents-on-the-server.md).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Almacenar en caché datos para su uso sin conexión o en un servidor](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Cómo: Almacenar en caché mediante programación un origen de datos en un documento de Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [Cómo: Almacenar datos en caché en un documento protegido por contraseña](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Tutorial: Crear a una relación de maestro/detalle con un conjunto de datos en caché](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)  
