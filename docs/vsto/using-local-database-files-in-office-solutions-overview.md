---
title: Usar archivos de base de datos local en información general sobre soluciones de Office
description: Obtenga información sobre cómo puede incluir un archivo de base de datos, como un archivo SQL Server Express (. MDF) o un archivo de acceso Microsoft Office (. mdb), en la solución de Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- data [Office development in Visual Studio], local
- local data [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 857038700a29f423250f006e743152bceea43c14
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838241"
---
# <a name="use-local-database-files-in-office-solutions-overview"></a>Usar archivos de base de datos local en información general sobre soluciones de Office
  Puede incluir un archivo de base de datos, como un archivo SQL Server Express (*. MDF*) o un archivo de acceso Microsoft Office (*. mdb*), en la solución de Office. Esto permite a los usuarios finales mantener una base de datos local en situaciones en las que no es necesario mantener una base de datos centralizada, por ejemplo, en una solución de inventario local que se utiliza en un solo equipo.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="import-the-database-file-into-a-project"></a>Importar el archivo de base de datos en un proyecto
 Para importar el archivo de base de datos en el proyecto, use el Asistente para la **configuración de orígenes de datos** para crear un origen de datos basado en el archivo de base de datos. El asistente agrega el archivo de base de datos y un conjunto de datos con tipo al proyecto.

## <a name="deploy-the-database-file"></a>Implementar el archivo de base de datos
 El **Asistente** para la configuración de orígenes de datos usa una ruta de acceso relativa para crear conexiones con el archivo de base de datos local. Esto le permite copiar la solución de un equipo a otro si mantiene las posiciones relativas de los archivos.

 Si implementa la solución en un servidor y, a continuación, distribuye el documento a cada usuario final, también debe distribuir manualmente el archivo de base de datos e instalarlo en la misma posición relativa al documento. Esto significa que el usuario final no puede mover el documento a una nueva ubicación en su equipo, a menos que también mueva el archivo de base de datos.

## <a name="local-database-files-and-caching-the-dataset"></a>Archivos de base de datos local y almacenamiento en caché del conjunto de datos
 En las soluciones de nivel de documento para Microsoft Office Excel y Microsoft Office Word, puede almacenar en caché los conjuntos de valores del documento marcando la instancia de DataSet con el atributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> . Al agregar el archivo de base de datos al proyecto mediante el **Asistente para la configuración de orígenes de datos**, se agrega automáticamente un conjunto de datos con tipo al proyecto. Rara vez es necesario aplicar <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> a este conjunto de datos, ya que los datos ya son locales en el equipo del usuario. Para obtener más información, vea [almacenar datos en caché](../vsto/caching-data.md).

## <a name="see-also"></a>Vea también
- [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Cómo: rellenar documentos con datos de una base de datos](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Cómo: actualizar un origen de datos con datos de un control host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)
- [Datos de caché](../vsto/caching-data.md)
