---
title: Especifique dónde desea copiar los archivos | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, specifying location
- Publish Location property
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ab842ce4f66684bf167d3cf627ce8cde82c5ea7c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53830380"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Procedimiento Especificar dónde copia Visual Studio los archivos
Al publicar una aplicación mediante ClickOnce, la propiedad `Publish Location` especifica la ubicación donde se colocan los archivos de la aplicación y el manifiesto. La ubicación puede ser una ruta de acceso de archivo o la ruta de acceso a un servidor FTP.  
  
 La `Publish Location` propiedad se puede especificar en la página **Publicar** del **Diseñador de proyectos** o mediante el Asistente para publicación. Para obtener más información, vea [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
> [!NOTE]
>  Cuando se instala más de una versión de una aplicación con ClickOnce, la instalación mueve las versiones anteriores de la aplicación a una carpeta llamada Archivo, en la ubicación de publicación que especifiques. Al archivar las versiones anteriores de esta manera, el directorio de instalación se mantiene limpio de carpetas de versiones anteriores.  
  
### <a name="to-specify-a-publishing-location"></a>Para especificar una ubicación de publicación  
  
1. Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2. Haga clic en la pestaña **Publicar**.  
  
3. En el campo **Ubicación de publicación**, escriba la ubicación de publicación mediante uno de los siguientes formatos:  
  
   - Para publicar en un recurso compartido de archivos o en una ruta de acceso de disco, escriba la ruta mediante una ruta de acceso UNC (*\\\Server\NombreAplicación*) o una ruta de acceso de archivo (*C:\Deploy\NombreAplicación*).  
  
   - Para publicar en un servidor FTP, escriba la ruta de acceso con el formato <em>ftp://ftp.microsoft.com/\<NombreAplicación></em>.  
  
     Tenga en cuenta que debe haber texto en el cuadro **Ubicación de publicación** para que el botón Examinar (**...**) funcione.  
  
## <a name="see-also"></a>Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)