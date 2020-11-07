---
title: Establecer la ubicación del archivo de registro personalizado (errores de implementación de ClickOnce)
description: Obtenga información sobre los archivos de registro de activación que ClickOnce mantiene para todas las implementaciones, que documentan los errores de instalación e inicialización de una implementación ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 3d9c8ce481ab9ca99b7d456f53418641654369ad
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351042"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Cómo: Establecer una ubicación de archivos de registro personalizada para los errores de implementaciones de ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mantiene los archivos de registro de activación de todas las implementaciones. Estos registros documentan los errores relacionados con la instalación e inicialización de una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación. De forma predeterminada, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] crea un archivo de registro para cada activación de implementación. Almacena estos archivos de registro en la carpeta archivos temporales de Internet. El archivo de registro de una implementación se muestra al usuario cuando se produce un error de activación y el usuario hace clic en **detalles** en el cuadro de diálogo de error resultante.

 Puede cambiar este comportamiento para un cliente específico mediante el editor del registro ( **regedit.exe** ) para establecer una ruta de acceso del archivo de registro personalizada. En este caso, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] registra la activación correcta y los errores de todas las implementaciones en un único archivo.

> [!CAUTION]
> utilizar el Editor del registro de configuraciones incorrectamente puede ocasionar problemas graves que quizás requieran reinstalar el sistema operativo. Use el Editor del Registro bajo su propia responsabilidad.

> [!NOTE]
> Tendrá que truncar o eliminar el archivo de registro en ocasiones para evitar que crezca demasiado.

 En el procedimiento siguiente se describe cómo establecer una ubicación de archivo de registro personalizada para un solo cliente.

### <a name="to-set-a-custom-log-file-location"></a>Para establecer una ubicación de archivo de registro personalizada

1. Abra **Regedit.exe**.

2. Navegue hasta el nodo `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment` .

3. Establezca el valor `LogFilePath` de cadena en la ruta de acceso completa y el nombre de archivo de la ubicación de registro personalizada que prefiera.

     Esta ubicación debe estar en un directorio en el que el usuario tenga acceso de escritura. Por ejemplo, en Windows Vista, cree la siguiente estructura de carpetas y establezca `LogFilePath` en *C:\Users \\ \<username> \Documents\Logs\ClickOnce\installation.log*.

## <a name="see-also"></a>Vea también
- [Solución de problemas de implementaciones de ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)