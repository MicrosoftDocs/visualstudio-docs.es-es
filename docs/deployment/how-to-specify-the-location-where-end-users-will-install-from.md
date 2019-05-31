---
title: Procedimiento Especifique la ubicación donde se instalarán los usuarios finales desde | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: bd447f0d68eb729c0bd25a65e99e871d7927c49b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62898589"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Procedimiento Especificación de la ubicación desde la que instalarán los usuarios finales
Al publicar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación, la ubicación donde los usuarios van a descargar e instalar la aplicación no es necesariamente la ubicación donde se publica inicialmente la aplicación. Por ejemplo, en algunas organizaciones, un desarrollador puede publicar una aplicación en un servidor de ensayo y, a continuación, un administrador podría mover la aplicación a un servidor Web.

 En este caso, puede usar el `Installation URL` propiedad para especificar el servidor Web donde los usuarios van a descargar la aplicación. Esto es necesario para que el manifiesto de aplicación sepa dónde buscar las actualizaciones.

 El `Installation URL` propiedad puede establecerse en el **publicar** página de la **Diseñador de proyectos**.

 **Tenga en cuenta** el `Installation URL` propiedad también puede establecerse utilizando la **Asistente para publicación**. Para obtener más información, vea [Cómo: Publicación de una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

### <a name="to-specify-an-installation-url"></a>Para especificar una dirección URL de instalación

1. Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.

2. Haga clic en la pestaña **Publicar**.

3. En el campo de dirección URL de instalación, escriba la ubicación de instalación mediante una dirección URL completa con el formato *http://www.microsoft.com/ApplicationName* , o una ruta UNC con el formato  *\\\Server\ApplicationName*.

## <a name="see-also"></a>Vea también
- [Cómo: Especificación de la ubicación en la que Visual Studio copia los archivos](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)
- [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)