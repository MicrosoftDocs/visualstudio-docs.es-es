---
title: "Uso de archivos de base de datos Local en información general sobre soluciones de Office | Documentos de Microsoft"
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
- Office applications [Office development in Visual Studio], data
- data [Office development in Visual Studio], local
- local data [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1576af3c3fc8a1c7f514a4941eb849df03774c5f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="using-local-database-files-in-office-solutions-overview"></a>Información general sobre el uso de archivos de bases de datos locales en soluciones de Office
  Puede incluir un archivo de base de datos, como un archivo SQL Server Express (.mdf) o un archivo de Microsoft Office Access (.mdb), en la solución de Office. Esto permite a los usuarios finales mantener una base de datos local en situaciones donde no es necesario, por ejemplo, en una solución de inventario local que se usa en un único equipo mantener una base de datos centralizada.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="importing-the-database-file-into-a-project"></a>Importar el archivo de base de datos en un proyecto  
 Para importar el archivo de base de datos en el proyecto, utilice la **Asistente para configuración de orígenes de datos** para crear un origen de datos basado en el archivo de base de datos. El asistente agrega el archivo de base de datos y un conjunto de datos con tipo al proyecto.  
  
## <a name="deploying-the-database-file"></a>Implementar el archivo de base de datos  
 El **Data Source Configuration Wizard** utiliza una ruta de acceso relativa para crear conexiones en el archivo de base de datos local. Esto le permite copiar la solución de un equipo a otro si mantiene las posiciones relativas de los archivos.  
  
 Si implementa la solución en un servidor y, a continuación, distribuye el documento a cada usuario final, debe distribuir el archivo de base de datos manualmente e instalarlo en la misma posición relativa al documento. Esto significa que el usuario final no se puede mover el documento a una nueva ubicación en su equipo, a menos que también pasa el archivo de base de datos.  
  
## <a name="local-database-files-and-caching-the-dataset"></a>Archivos de base de datos local y el almacenamiento en caché el conjunto de datos  
 En las soluciones de nivel de documento para Microsoft Office Excel y Microsoft Office Word, puede almacenar en caché conjuntos de datos en el documento marcando la instancia del conjunto de datos con el atributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>. Al agregar el archivo de base de datos al proyecto mediante el uso de la **Asistente para configuración de orígenes de datos**, un conjunto de datos con tipo se agrega automáticamente al proyecto. Es raro que deba aplicar <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> a este conjunto de datos, porque los datos ya son locales en el equipo del usuario. Para obtener más información, consulta [Caching Data](../vsto/caching-data.md).  
  
## <a name="see-also"></a>Vea también  
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Cómo: rellenar documentos con datos de una base de datos](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Cómo: actualizar un origen de datos con datos de un Control Host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)   
 [Almacenamiento de datos en caché](../vsto/caching-data.md)  
  
  