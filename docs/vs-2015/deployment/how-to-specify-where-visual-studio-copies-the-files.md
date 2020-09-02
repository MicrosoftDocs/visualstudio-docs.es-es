---
title: 'Cómo: especificar dónde Visual Studio 2015 copia archivos | Microsoft Docs'
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, specifying location
- Publish Location property
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8759145dd4a7647cad6e9964ae1f1c97d333b626
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65226162"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Cómo: Especificar dónde Visual Studio copia los archivos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al publicar una aplicación mediante ClickOnce, la propiedad `Publish Location` especifica la ubicación donde se colocan los archivos de la aplicación y el manifiesto. La ubicación puede ser una ruta de acceso de archivo o la ruta de acceso a un servidor FTP.

 La `Publish Location` propiedad se puede especificar en la página **Publicar** del **Diseñador de proyectos** o mediante el Asistente para publicación. Para obtener más información, consulte [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

> [!NOTE]
> Cuando se instala más de una versión de una aplicación con ClickOnce, la instalación mueve las versiones anteriores de la aplicación a una carpeta llamada Archivo, en la ubicación de publicación que especifiques. Al archivar las versiones anteriores de esta manera, el directorio de instalación se mantiene limpio de carpetas de versiones anteriores.

### <a name="to-specify-a-publishing-location"></a>Para especificar una ubicación de publicación

1. Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.

2. Haga clic en la pestaña **Publicar**.

3. En el campo **Ubicación de publicación**, escriba la ubicación de publicación mediante uno de los siguientes formatos:

   - Para publicar en un recurso compartido de archivos o en una ruta de acceso de disco, escriba la ruta de acceso mediante una ruta de acceso UNC ( \\ \Server\ApplicationName) o una ruta de acceso de archivo (C:\Deploy\ApplicationName).

   - Para publicar en un servidor FTP, escriba la ruta de acceso con el formato FTP: \/ /FTP.Microsoft.com/ApplicationName.

     Tenga en cuenta que el texto debe estar presente en el cuadro **Ubicación de publicación** para que el botón Examinar (**...**) funcione.

## <a name="see-also"></a>Consulte también
 Publicar [aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md) [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
