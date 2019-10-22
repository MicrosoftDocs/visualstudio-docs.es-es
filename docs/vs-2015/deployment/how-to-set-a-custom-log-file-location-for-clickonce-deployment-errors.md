---
title: Procedimiento Establecer una ubicación de archivo de registro personalizado para los errores de implementación ClickOnce | Documentos de Microsoft
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63403548"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Procedimiento Establecer una ubicación de archivos de registro personalizada para los errores de implementaciones ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] mantiene los archivos de registro de activación para todas las implementaciones. Estos registros documentan los errores que pertenecen a instalar e inicializar un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implementación. De forma predeterminada, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] crea un archivo de registro para cada activación de la implementación. Estos archivos de registro almacena en la carpeta archivos temporales de Internet. El archivo de registro para una implementación se muestra al usuario cuando se produce un error de activación y el usuario hace clic **detalles** en el cuadro de diálogo de error resultante.  
  
 Puede cambiar este comportamiento para un cliente específico mediante el Editor del registro (**regedit.exe**) para establecer una ruta de acceso del archivo de registro personalizado. En este caso, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] registros de activación aciertos y errores para todas las implementaciones en un único archivo.  
  
> [!CAUTION]
> Si utiliza incorrectamente el Editor del registro, puede provocar problemas graves que quizás requieran reinstalar el sistema operativo. Use el Editor del Registro bajo su propia responsabilidad.  
  
> [!NOTE]
> Deberá trunque o elimine el archivo de registro en ocasiones, para evitar que crezca demasiado.  
  
 El siguiente procedimiento describe cómo establecer una ubicación de archivo de registro personalizado para un solo cliente.  
  
### <a name="to-set-a-custom-log-file-location"></a>Para establecer una ubicación de archivo de registro personalizado  
  
1. Abra **Regedit.exe**.  
  
2. Desplácese hasta el nodo `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3. Establezca el valor de cadena `LogFilePath` a la ruta de acceso completa y el nombre de la ubicación de registro personalizada que prefiera.  
  
     Esta ubicación debe estar en un directorio al que el usuario tiene acceso de escritura. Por ejemplo, en Windows Vista, cree la siguiente estructura de carpetas y establecer `LogFilePath` a C:\Users\\< nombre de usuario\>\Documents\Logs\ClickOnce\installation.log.  
  
## <a name="see-also"></a>Vea también  
 [Solucionar problemas en implementaciones ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
