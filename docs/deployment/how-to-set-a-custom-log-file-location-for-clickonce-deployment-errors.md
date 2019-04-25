---
title: Procedimiento Establecer una ubicación de archivo de registro personalizado para los errores de implementación ClickOnce | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- ClickOnce deployment, error logging
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0c4f3b6243e7deb7ef6040cb717de04660d6687d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60065628"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Procedimiento Establecimiento de una ubicación de archivos de registro personalizada para los errores de implementaciones de ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mantiene los archivos de registro de activación para todas las implementaciones. Estos registros documentan los errores que pertenecen a instalar e inicializar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación. De forma predeterminada, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] crea un archivo de registro para cada activación de la implementación. Estos archivos de registro almacena en la carpeta archivos temporales de Internet. El archivo de registro para una implementación se muestra al usuario cuando se produce un error de activación y el usuario hace clic **detalles** en el cuadro de diálogo de error resultante.

 Puede cambiar este comportamiento para un cliente específico mediante el Editor del registro (**regedit.exe**) para establecer una ruta de acceso del archivo de registro personalizado. En este caso, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] registros de activación aciertos y errores para todas las implementaciones en un único archivo.

> [!CAUTION]
>  Si utiliza incorrectamente el Editor del registro, puede provocar problemas graves que quizás requieran reinstalar el sistema operativo. Use el Editor del Registro bajo su propia responsabilidad.

> [!NOTE]
>  Deberá trunque o elimine el archivo de registro en ocasiones, para evitar que crezca demasiado.

 El siguiente procedimiento describe cómo establecer una ubicación de archivo de registro personalizado para un solo cliente.

### <a name="to-set-a-custom-log-file-location"></a>Para establecer una ubicación de archivo de registro personalizado

1. Abra **Regedit.exe**.

2. Desplácese hasta el nodo `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.

3. Establezca el valor de cadena `LogFilePath` a la ruta de acceso completa y el nombre de la ubicación de registro personalizada que prefiera.

     Esta ubicación debe estar en un directorio al que el usuario tiene acceso de escritura. Por ejemplo, en Windows Vista, cree la siguiente estructura de carpetas y establecer `LogFilePath` a *C:\Users\\\<username > \Documents\Logs\ClickOnce\installation.log*.

## <a name="see-also"></a>Vea también
- [Solución de problemas de implementaciones de ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)