---
title: 'Cómo: especificar la ubicación desde la que se instalarán los usuarios finales | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 82181d906adc3454dfe77ef4fb21d8bdf99df16f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "77557991"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Cómo: Especificar la ubicación desde la que instalarán los usuarios finales
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al publicar una [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación, la ubicación en la que los usuarios van a descargar e instalar la aplicación no es necesariamente la ubicación en la que se publica la aplicación inicialmente. Por ejemplo, en algunas organizaciones un desarrollador puede publicar una aplicación en un servidor de ensayo y, a continuación, un administrador podría trasladar la aplicación a un servidor Web.  
  
 En este caso, puede usar la `Installation URL` propiedad para especificar el servidor Web en el que los usuarios van a descargar la aplicación. Esto es necesario para que el manifiesto de aplicación sepa dónde buscar las actualizaciones.  
  
 La `Installation URL` propiedad se puede establecer en la página **publicar** del **Diseñador de proyectos**.  
  
 **Nota:** La `Installation URL` propiedad también se puede establecer mediante **Asistente para publicación**. Para obtener más información, consulte [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-specify-an-installation-url"></a>Para especificar una dirección URL de instalación  
  
1. Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2. Haga clic en la pestaña **Publicar**.  
  
3. En el campo dirección URL de instalación, escriba la ubicación de instalación mediante una dirección URL completa con el formato `https://www.contoso.com/ApplicationName` o una ruta de acceso UNC con el formato `\\Server\ApplicationName` .  
  
## <a name="see-also"></a>Consulte también  
 [Cómo: especificar dónde Visual Studio copia los archivos](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicación de una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
