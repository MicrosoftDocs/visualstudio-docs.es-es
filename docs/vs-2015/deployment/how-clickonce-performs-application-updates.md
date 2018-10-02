---
title: Cómo realiza ClickOnce actualizaciones de aplicaciones | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- updates, ClickOnce
- ClickOnce deployment, updates
- deploying applications [ClickOnce], application updates
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 8011447de248c2dbcdbd513dc4e51106ceb3a568
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47582523"
---
# <a name="how-clickonce-performs-application-updates"></a>Cómo realiza ClickOnce actualizaciones de aplicaciones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [cómo ClickOnce realiza actualizaciones de la aplicación](https://docs.microsoft.com/visualstudio/deployment/how-clickonce-performs-application-updates).  
  
ClickOnce usa la información de versión del archivo especificada en el manifiesto de implementación de una aplicación para decidir si desea actualizar los archivos de la aplicación. Una vez que inicia una actualización, ClickOnce usa una técnica denominada *revisión de archivos* para evitar la descarga con redundancia de los archivos de aplicación.  
  
## <a name="file-patching"></a>Revisión de archivos  
 Al actualizar una aplicación, ClickOnce no descargar todos los archivos para la nueva versión de la aplicación a menos que los archivos han cambiado. En su lugar, compara el hash de las firmas de los archivos especificados en el manifiesto de aplicación para la aplicación actual con las firmas en el manifiesto para la nueva versión. Si las firmas de un archivo son diferentes, ClickOnce descarga la nueva versión. Si las firmas coinciden, el archivo no ha cambiado de una versión a la siguiente. En este caso, ClickOnce copia el archivo existente y lo utiliza en la nueva versión de la aplicación. Este enfoque evita que ClickOnce de tener que descargar toda la aplicación de nuevo, incluso si sólo uno o dos archivos han cambiado.  
  
 Revisión de archivos también funciona para los ensamblados que se descargan a petición mediante el <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> y <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> métodos.  
  
 Si usa Visual Studio para compilar su aplicación, generará nuevas firmas hash para todos los archivos cada vez que se vuelve a generar todo el proyecto. En este caso, se descargarán todos los ensamblados en el cliente, aunque algunos ensamblados solo pueden haber cambiado.  
  
 Revisión de archivos no funciona para los archivos que están marcados como datos y se almacenan en el directorio de datos. Se descargan siempre, independientemente de la firma del archivo hash. Para obtener más información sobre el directorio de datos, vea [obtener acceso Local y remota de datos en aplicaciones ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
## <a name="see-also"></a>Vea también  
 [Elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Elegir una estrategia de implementación ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)



