---
title: Especificar la ubicación desde la que se instalarán los usuarios finales
description: Obtenga información sobre cómo establecer la propiedad de la dirección URL de instalación, que es donde se hospeda una aplicación ClickOnce publicada para su instalación.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying an installation URL
- URLs, specifying an installation URL
- installation, specifying installation an URL
- Installation URL property
ms.assetid: 04a804bf-ed55-4a7a-a1e6-f63ed99c0276
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3518a2eef331414e5c73c0cebb36681ad2b72d61
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349625"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Cómo: Especificar la ubicación desde la que instalarán los usuarios finales

Al publicar una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación, la ubicación en la que los usuarios van a descargar e instalar la aplicación no es necesariamente la ubicación en la que se publica la aplicación inicialmente. Por ejemplo, en algunas organizaciones un desarrollador puede publicar una aplicación en un servidor de ensayo y, a continuación, un administrador podría trasladar la aplicación a un servidor Web.

En este caso, puede usar la `Installation URL` propiedad para especificar el servidor Web en el que los usuarios van a descargar la aplicación. Esto es necesario para que el manifiesto de aplicación sepa dónde buscar las actualizaciones.

La `Installation URL` propiedad se puede establecer en la página **publicar** del **Diseñador de proyectos**.

> [!NOTE]
> La `Installation URL` propiedad también se puede establecer mediante **Asistente para publicación**. Para obtener más información, consulte [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

### <a name="to-specify-an-installation-url"></a>Para especificar una dirección URL de instalación

1. Seleccione un proyecto en el **Explorador de soluciones** y, en el menú **Proyecto** , haga clic en **Propiedades**.

2. Haga clic en la pestaña **Publicar**.

3. En el campo dirección URL de instalación, escriba la ubicación de instalación mediante una dirección URL completa con el formato `https://www.contoso.com/ApplicationName` o una ruta de acceso UNC con el formato `\Server\ApplicationName` .

## <a name="see-also"></a>Vea también
- [Cómo: Especificar dónde Visual Studio copia los archivos](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)
- [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)