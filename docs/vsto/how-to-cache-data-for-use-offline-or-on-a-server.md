---
title: "Cómo: almacenar en caché datos para su uso sin conexión o en un servidor | Documentos de Microsoft"
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
- data caching [Office development in Visual Studio], server use
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- offline data [Office development in Visual Studio]
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio], offline use
ms.assetid: 6246b187-9413-4336-821d-2259b1adec5a
caps.latest.revision: "49"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 07d467d67c78f6779a8be2d21b266f8328e30ff7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>Cómo: Almacenar datos en la memoria caché para el uso sin conexión o en un servidor
  Puede marcar un elemento de datos en la memoria caché en el documento, para que esté disponible sin conexión. Esto también permite para los datos en el documento para su manipulación por otro código cuando el documento está almacenado en un servidor.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Puede marcar un elemento de datos en la memoria caché cuando se declara el elemento de datos en el código o, si está utilizando un <xref:System.Data.DataSet>, estableciendo una propiedad el **propiedades** ventana. Si está almacenando en caché un elemento de datos que no es un <xref:System.Data.DataSet> o <xref:System.Data.DataTable>, asegúrese de que cumple los criterios para que se almacenó en caché en el documento. Para obtener más información, consulta [Caching Data](../vsto/caching-data.md).  
  
> [!NOTE]  
>  Conjuntos de datos creados con Visual Basic que están marcados como **en caché** y **WithEvents** (incluidos los conjuntos de datos que se arrastran desde el **orígenes de datos** ventana o **Cuadro de herramientas** que tienen la **CacheInDocument** propiedad establecida en **True**) tiene un carácter de subrayado como prefijo a sus nombres en la memoria caché. Por ejemplo, si crea un conjunto de datos y asígnele el nombre **clientes**, <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> nombre será **_Clientes** en la memoria caché. Cuando usas <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> para tener acceso a este elemento almacenado en caché, debe especificar **_Clientes** en lugar de **clientes**.  
  
### <a name="to-cache-data-in-the-document-using-code"></a>Para almacenar datos en el documento mediante código  
  
1.  Declare un campo público o una propiedad para el elemento de datos como un miembro de una clase de elemento host en el proyecto, como el `ThisDocumen`clase t en un proyecto de Word o el `ThisWorkbook` clase en un proyecto de Excel.  
  
2.  Aplicar el <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atributo al miembro para marcar el elemento de datos que se almacenarán en caché de datos del documento. En el ejemplo siguiente se aplica este atributo a una declaración de campo para un <xref:System.Data.DataSet>.  
  
     [!code-csharp[Trin_VstcoreDataExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#11)]  
  
3.  Agregue código para crear una instancia del elemento de datos y, si procede, realizar la carga desde la base de datos.  
  
     El elemento de datos solo se carga cuando se crea por primera vez; por lo tanto, la memoria caché permanece con el documento y se debe escribir otro código para actualizarlo.  
  
### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>Para almacenar en caché un conjunto de datos en el documento mediante la ventana Propiedades  
  
1.  Agregar el conjunto de datos al proyecto mediante el uso de herramientas en el Diseñador de Visual Studio, por ejemplo, mediante la adición de un origen de datos al proyecto mediante el **orígenes de datos** ventana.  
  
2.  Cree una instancia del conjunto de datos si aún no tiene uno y seleccione la instancia en el diseñador.  
  
3.  En el **propiedades** ventana, establezca el **CacheInDocument** propiedad **True**.  
  
     Para obtener más información, consulte [propiedades en proyectos de Office](../vsto/properties-in-office-projects.md).  
  
4.  En el **propiedades** ventana, establezca el **modificadores** propiedad **público** (de forma predeterminada es **interno**).  
  
## <a name="see-also"></a>Vea también  
 [Almacenar datos en caché](../vsto/caching-data.md)   
 [Cómo: almacenar en memoria caché un origen de datos en un documento de Office mediante programación](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [Cómo: almacenar en caché datos en un documento protegido por contraseña](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Obtener acceso a datos de documentos en el servidor](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Guardar datos](/visualstudio/data-tools/saving-data)  
  
  