---
title: 'Cómo: especificar la ubicación donde se instalarán los usuarios finales desde | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: wpickett
ms.openlocfilehash: 113356a664d94fdd2e8d3e53fae6025d8ef22e60
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49213010"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Cómo: Especificar la ubicación desde la que instalarán los usuarios finales
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al publicar un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación, la ubicación donde los usuarios van a descargar e instalar la aplicación no es necesariamente la ubicación donde se publica inicialmente la aplicación. Por ejemplo, en algunas organizaciones, un desarrollador puede publicar una aplicación en un servidor de ensayo y, a continuación, un administrador podría mover la aplicación a un servidor Web.  
  
 En este caso, puede usar el `Installation URL` propiedad para especificar el servidor Web donde los usuarios van a descargar la aplicación. Esto es necesario para que el manifiesto de aplicación sepa dónde buscar las actualizaciones.  
  
 El `Installation URL` propiedad puede establecerse en el **publicar** página de la **Diseñador de proyectos**.  
  
 **Tenga en cuenta** el `Installation URL` propiedad también puede establecerse utilizando la **Asistente para publicación**. Para obtener más información, consulte [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-specify-an-installation-url"></a>Para especificar una dirección URL de instalación  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en el **publicar** ficha.  
  
3.  En el campo de dirección URL de instalación, escriba la ubicación de instalación mediante una dirección URL completa con el formato http://www.microsoft.com/ApplicationName, o una ruta UNC con el formato \\\Server\ApplicationName.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Especificar dónde Visual Studio copia los archivos](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)



