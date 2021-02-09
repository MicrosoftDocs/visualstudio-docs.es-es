---
title: Especifique dónde desea copiar los archivos | Microsoft Docs
description: Obtenga información sobre cómo establecer la propiedad ubicación de publicación para una aplicación ClickOnce, que especifica la ubicación donde se colocan los archivos y el manifiesto de la aplicación.
ms.custom:
- SEO-VS-2020
- seodec18
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 50f3e5d8500e57dd336919a5da58af094db97169
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887424"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Cómo: Especificar dónde Visual Studio copia los archivos
Al publicar una aplicación mediante ClickOnce, la propiedad `Publish Location` especifica la ubicación donde se colocan los archivos de la aplicación y el manifiesto. La ubicación puede ser una ruta de acceso de archivo o la ruta de acceso a un servidor FTP.

 La `Publish Location` propiedad se puede especificar en la página **Publicar** del **Diseñador de proyectos** o mediante el Asistente para publicación. Para obtener más información, consulte [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

> [!NOTE]
> Cuando se instala más de una versión de una aplicación con ClickOnce, la instalación mueve las versiones anteriores de la aplicación a una carpeta llamada Archivo, en la ubicación de publicación que especifiques. Al archivar las versiones anteriores de esta manera, el directorio de instalación se mantiene limpio de carpetas de versiones anteriores.

### <a name="to-specify-a-publishing-location"></a>Para especificar una ubicación de publicación

1. Seleccione un proyecto en el **Explorador de soluciones** y, en el menú **Proyecto** , haga clic en **Propiedades**.

2. Haga clic en la pestaña **Publicar**.

3. En el campo **Ubicación de publicación**, escriba la ubicación de publicación mediante uno de los siguientes formatos:

   - Para publicar en un recurso compartido de archivos o en una ruta de acceso de disco, escriba la ruta de acceso mediante una ruta de acceso UNC (*\\ \Server\ApplicationName*) o una ruta de acceso de archivo (*C:\Deploy\ApplicationName*).

   - Para publicar en un servidor FTP, escriba la ruta de acceso con el formato <em>FTP://ftp.Microsoft.com/ \<ApplicationName> </em>.

     Tenga en cuenta que el texto debe estar presente en el cuadro **Ubicación de publicación** para que el botón Examinar (**...**) funcione.

## <a name="see-also"></a>Vea también
- [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)