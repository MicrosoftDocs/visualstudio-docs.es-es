---
title: 'Cómo: especificar la ubicación donde se instalarán los usuarios finales desde | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0152cf6b03f2e089ee8633ef4abae9043e41bc24
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Cómo: Especificar la ubicación desde la que instalarán los usuarios finales
Al publicar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación, la ubicación donde los usuarios van a descargar e instalar la aplicación no es necesariamente la ubicación donde se publica inicialmente la aplicación. Por ejemplo, en algunas organizaciones un desarrollador puede publicar una aplicación en un servidor de ensayo y, a continuación, un administrador movería la aplicación a un servidor Web.  
  
 En este caso, puede usar el `Installation URL` propiedad para especificar el servidor Web donde los usuarios irán a descargar la aplicación. Esto es necesario para que el manifiesto de aplicación sepa dónde buscar actualizaciones.  
  
 El `Installation URL` propiedad puede establecerse en el **publicar** página de la **Diseñador de proyectos**.  
  
 **Tenga en cuenta** el `Installation URL` propiedad también puede establecerse utilizando la **PublishWizard**. Para obtener más información, consulte [Cómo: publicar una aplicación ClickOnce sin usar el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-specify-an-installation-url"></a>Para especificar una dirección URL de instalación  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en el **publicar** ficha.  
  
3.  En el campo de dirección URL de instalación, especifique la ubicación de instalación mediante una dirección URL completa con el formato http://www.microsoft.com/ApplicationName, o una ruta de acceso UNC con el formato \\\Server\ApplicationName.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Especificar dónde Visual Studio copia los archivos](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)