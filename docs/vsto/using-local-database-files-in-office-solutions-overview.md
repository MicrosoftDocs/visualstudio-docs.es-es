---
title: Usar archivos de base de datos local en información general sobre soluciones de Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- data [Office development in Visual Studio], local
- local data [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 527b2e2561b89dc38e56c0d9d854034a791edf19
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53939205"
---
# <a name="use-local-database-files-in-office-solutions-overview"></a>Usar archivos de base de datos local en información general sobre soluciones de Office
  Puede incluir un archivo de base de datos, como SQL Server Express (*.mdf*) archivo o Microsoft Office Access (*.mdb*) archivo en la solución de Office. Esto permite a los usuarios finales mantener una base de datos local en situaciones donde no es necesario, por ejemplo, en una solución de inventario local que se usa en un único equipo mantiene una base de datos centralizada.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="import-the-database-file-into-a-project"></a>Importar el archivo de base de datos en un proyecto  
 Para importar el archivo de base de datos en el proyecto, utilice el **Asistente para configuración de origen de datos** para crear un origen de datos basado en el archivo de base de datos. El asistente agrega el archivo de base de datos y un conjunto de datos con tipo al proyecto.  
  
## <a name="deploy-the-database-file"></a>Implementar el archivo de base de datos  
 El **Asistente para configuración de origen de datos** utiliza una ruta de acceso relativa para crear conexiones en el archivo de base de datos local. Esto le permite copiar la solución de un equipo a otro si mantiene las posiciones relativas de los archivos.  
  
 Si implementa la solución en un servidor y, a continuación, distribuye el documento a cada usuario final, también manualmente debe distribuir el archivo de base de datos e instalarlo en la misma posición relativa al documento. Esto significa que el usuario final no se puede mover el documento a una nueva ubicación en su equipo, a menos que también se mueve el archivo de base de datos.  
  
## <a name="local-database-files-and-caching-the-dataset"></a>Archivos de base de datos local y el almacenamiento en caché el conjunto de datos  
 En las soluciones de nivel de documento para Microsoft Office Excel y Microsoft Office Word, puede almacenar en caché conjuntos de datos en el documento al marcar la instancia de conjunto de datos con el atributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>. Al agregar el archivo de base de datos al proyecto mediante el uso de la **Asistente para configuración de origen de datos**, un conjunto de datos con tipo se agrega automáticamente al proyecto. Es raro tener aplicar <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> a este conjunto de datos, porque los datos ya son locales en el equipo del usuario. Para obtener más información, consulte [almacenar en caché datos](../vsto/caching-data.md).  
  
## <a name="see-also"></a>Vea también  
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Cómo: Rellenar documentos con datos de una base de datos](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Cómo: Actualizar un origen de datos con datos de un control host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)   
 [Almacenar datos en caché](../vsto/caching-data.md)  
