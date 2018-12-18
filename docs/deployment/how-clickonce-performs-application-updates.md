---
title: Cómo realiza ClickOnce actualizaciones de aplicaciones | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- updates, ClickOnce
- ClickOnce deployment, updates
- deploying applications [ClickOnce], application updates
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a1f5d9b67633ffa2b14f780b9588f526372a4f5d
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/19/2018
ms.locfileid: "39152524"
---
# <a name="how-clickonce-performs-application-updates"></a>Cómo realiza ClickOnce actualizaciones de aplicaciones
ClickOnce usa la información de versión del archivo especificada en el manifiesto de implementación de una aplicación para decidir si desea actualizar los archivos de la aplicación. Una vez que inicia una actualización, ClickOnce usa una técnica denominada *revisión de archivos* para evitar la descarga con redundancia de los archivos de aplicación.  
  
## <a name="file-patching"></a>Revisión de archivos  
 Al actualizar una aplicación, ClickOnce no descargar todos los archivos para la nueva versión de la aplicación a menos que los archivos han cambiado. En su lugar, compara el hash de las firmas de los archivos especificados en el manifiesto de aplicación para la aplicación actual con las firmas en el manifiesto para la nueva versión. Si las firmas de un archivo son diferentes, ClickOnce descarga la nueva versión. Si las firmas coinciden, el archivo no ha cambiado de una versión a la siguiente. En este caso, ClickOnce copia el archivo existente y lo utiliza en la nueva versión de la aplicación. Este enfoque evita que ClickOnce de tener que descargar toda la aplicación de nuevo, incluso si sólo uno o dos archivos han cambiado.  
  
 Revisión de archivos también funciona para los ensamblados que se descargan a petición mediante el <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> y <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> métodos.  
  
 Si usa Visual Studio para compilar su aplicación, generará nuevas firmas hash para todos los archivos cada vez que se vuelve a generar todo el proyecto. En este caso, se descargarán todos los ensamblados en el cliente, aunque algunos ensamblados solo pueden haber cambiado.  
  
 Revisión de archivos no funciona para los archivos que están marcados como datos y se almacenan en el directorio de datos. Se descargan siempre, independientemente de la firma del archivo hash. Para obtener más información sobre el directorio de datos, vea [tener acceso a datos locales y remotos en aplicaciones ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
## <a name="see-also"></a>Vea también  
 [Elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Elegir una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)