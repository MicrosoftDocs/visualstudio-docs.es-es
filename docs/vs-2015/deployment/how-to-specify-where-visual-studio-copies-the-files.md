---
title: Procedimiento Especificar dónde Visual Studio 2015 copia los archivos | Microsoft Docs
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
ms.openlocfilehash: 5d36c5dafa37673263ab13dc46c7f02e44448fd8
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441610"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Procedimiento Especificar dónde Visual Studio copia los archivos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al publicar una aplicación mediante ClickOnce, la propiedad `Publish Location` especifica la ubicación donde se colocan los archivos de la aplicación y el manifiesto. La ubicación puede ser una ruta de acceso de archivo o la ruta de acceso a un servidor FTP.

 La `Publish Location` propiedad se puede especificar en la página **Publicar** del **Diseñador de proyectos** o mediante el Asistente para publicación. Para obtener más información, vea [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

> [!NOTE]
> Cuando se instala más de una versión de una aplicación con ClickOnce, la instalación mueve las versiones anteriores de la aplicación a una carpeta llamada Archivo, en la ubicación de publicación que especifiques. Al archivar las versiones anteriores de esta manera, el directorio de instalación se mantiene limpio de carpetas de versiones anteriores.

### <a name="to-specify-a-publishing-location"></a>Para especificar una ubicación de publicación

1. Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.

2. Haga clic en la pestaña **Publicar**.

3. En el campo **Ubicación de publicación**, escriba la ubicación de publicación mediante uno de los siguientes formatos:

   - Para publicar en una ruta de acceso de disco o recurso compartido de archivo, escriba la ruta de acceso mediante una ruta de acceso UNC (\\\Server\ApplicationName) o una ruta de acceso de archivo (C:\Deploy\ApplicationName).

   - Para publicar en un servidor FTP, escriba la ruta de acceso con el formato ftp://ftp.microsoft.com/NombreAplicación.

     Tenga en cuenta que debe haber texto en el cuadro **Ubicación de publicación** para que el botón Examinar (**...**) funcione.

## <a name="see-also"></a>Vea también
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md) [Cómo: Publicación de una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
