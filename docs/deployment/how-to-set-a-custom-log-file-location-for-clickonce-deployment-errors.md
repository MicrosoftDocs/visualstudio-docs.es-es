---
title: 'Cómo: establecer una ubicación de archivo de registro personalizado para los errores de implementación de ClickOnce | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 647eed5145d9d80f9fc62249763726a5940a7345
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
ms.locfileid: "31565723"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Cómo: Establecer una ubicación de archivos de registro personalizada para los errores de implementaciones de ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mantiene los archivos de registro de activación para todas las implementaciones. Estos registros documentan cualquier error relacionado con la instalación e inicialización de un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación. De forma predeterminada, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] crea un archivo de registro para cada activación de implementación. Estos archivos de registro almacena en la carpeta de archivos temporales de Internet. El archivo de registro para una implementación se muestra al usuario cuando se produce un error de activación y el usuario hace clic en **detalles** en el cuadro de diálogo de error resultante.  
  
 Puede cambiar este comportamiento para un cliente específico mediante el Editor del registro (**regedit.exe**) para establecer una ruta de acceso del archivo de registro personalizado. En este caso, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] registra activación correctas y erróneas para todas las implementaciones en un único archivo.  
  
> [!CAUTION]
>  Si utiliza incorrectamente el Editor del registro, puede provocar problemas graves que quizás requieran reinstalar el sistema operativo. Use el Editor del Registro bajo su propia responsabilidad.  
  
> [!NOTE]
>  Necesitará truncar o eliminar el archivo de registro en ocasiones, para evitar que crezca demasiado grande.  
  
 El siguiente procedimiento describe cómo establecer una ubicación de archivo de registro personalizado para un solo cliente.  
  
### <a name="to-set-a-custom-log-file-location"></a>Para establecer una ubicación de archivo de registro personalizada  
  
1.  Abra **Regedit.exe**.  
  
2.  Desplácese hasta el nodo `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Establezca el valor de cadena `LogFilePath` a la ruta de acceso completa y el nombre de la ubicación de registro personalizada que prefiera.  
  
     Esta ubicación debe estar en un directorio al que el usuario tiene acceso de escritura. Por ejemplo, en Windows Vista, cree la siguiente estructura de carpetas y establecer `LogFilePath` a C:\Users\\< nombre de usuario\>\Documents\Logs\ClickOnce\installation.log.  
  
## <a name="see-also"></a>Vea también  
 [Solucionar problemas en implementaciones ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)