---
title: 'Cómo: establecer una ubicación de archivo de registro personalizada para los errores de implementación de ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7a1b7c93e4b30bbfd373a5fad9d7001452d4f587
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842602"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Cómo: Establecer una ubicación de archivos de registro personalizada para los errores de implementaciones de ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] mantiene los archivos de registro de activación de todas las implementaciones. Estos registros documentan los errores relacionados con la instalación e inicialización de una [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implementación. De forma predeterminada, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] crea un archivo de registro para cada activación de implementación. Almacena estos archivos de registro en la carpeta archivos temporales de Internet. El archivo de registro de una implementación se muestra al usuario cuando se produce un error de activación y el usuario hace clic en **detalles** en el cuadro de diálogo de error resultante.  
  
 Puede cambiar este comportamiento para un cliente específico mediante el editor del registro (**regedit.exe**) para establecer una ruta de acceso del archivo de registro personalizada. En este caso, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] registra la activación correcta y los errores de todas las implementaciones en un único archivo.  
  
> [!CAUTION]
> utilizar el Editor del registro de configuraciones incorrectamente puede ocasionar problemas graves que quizás requieran reinstalar el sistema operativo. Use el Editor del Registro bajo su propia responsabilidad.  
  
> [!NOTE]
> Tendrá que truncar o eliminar el archivo de registro en ocasiones para evitar que crezca demasiado.  
  
 En el procedimiento siguiente se describe cómo establecer una ubicación de archivo de registro personalizada para un solo cliente.  
  
### <a name="to-set-a-custom-log-file-location"></a>Para establecer una ubicación de archivo de registro personalizada  
  
1. Abra **Regedit.exe**.  
  
2. Navegue hasta el nodo `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment` .  
  
3. Establezca el valor `LogFilePath` de cadena en la ruta de acceso completa y el nombre de archivo de la ubicación de registro personalizada que prefiera.  
  
     Esta ubicación debe estar en un directorio en el que el usuario tenga acceso de escritura. Por ejemplo, en Windows Vista, cree la siguiente estructura de carpetas y establezca `LogFilePath` en C:\Users \\<nombredeusuario \> \Documents\Logs\ClickOnce\installation.log.  
  
## <a name="see-also"></a>Consulte también  
 [Solucionar problemas en implementaciones ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
