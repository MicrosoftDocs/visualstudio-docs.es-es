---
title: Cómo realiza ClickOnce las actualizaciones de aplicaciones | Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9217558c68d47ef8f2bf34b10db16463ee76f857
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62900030"
---
# <a name="how-clickonce-performs-application-updates"></a>Cómo ClickOnce realiza actualizaciones de aplicaciones
ClickOnce usa la información de versión de archivo especificada en el manifiesto de implementación de una aplicación para decidir si se deben actualizar los archivos de la aplicación. Una vez que se inicia una actualización, ClickOnce utiliza una técnica denominada aplicación de *revisión de archivos* para evitar la descarga redundante de archivos de aplicación.

## <a name="file-patching"></a>Revisión de archivos
 Al actualizar una aplicación, ClickOnce no descarga todos los archivos de la nueva versión de la aplicación a menos que hayan cambiado los archivos. En su lugar, compara las firmas hash de los archivos especificados en el manifiesto de aplicación para la aplicación actual con las firmas del manifiesto de la nueva versión. Si las firmas de un archivo son diferentes, ClickOnce descarga la nueva versión. Si las firmas coinciden, el archivo no ha cambiado de una versión a otra. En este caso, ClickOnce copia el archivo existente y lo usa en la nueva versión de la aplicación. Este enfoque evita que ClickOnce tenga que volver a descargar toda la aplicación, incluso si solo uno o dos archivos han cambiado.

 La revisión de archivos también funciona para los ensamblados que se descargan a petición mediante los <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> métodos y.

 Si usa Visual Studio para compilar la aplicación, se generarán nuevas firmas hash para todos los archivos cada vez que Recompile todo el proyecto. En este caso, todos los ensamblados se descargarán en el cliente, aunque solo algunos ensamblados pueden haber cambiado.

 La revisión de archivos no funciona para los archivos marcados como datos y almacenados en el directorio de datos. Siempre se descargan independientemente de la firma de hash del archivo. Para obtener más información sobre el directorio de datos, vea [acceso a datos locales y remotos en aplicaciones ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

## <a name="see-also"></a>Consulte también
- [Selección de una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Selección de una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)