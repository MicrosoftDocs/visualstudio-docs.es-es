---
title: "C&#243;mo: Establecer una ubicaci&#243;n de archivos de registro personalizada para los errores de implementaciones de ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "implementación ClickOnce, registro de errores"
  - "implementación ClickOnce, solucionar problemas"
  - "solucionar problemas en implementaciones ClickOnce"
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# C&#243;mo: Establecer una ubicaci&#243;n de archivos de registro personalizada para los errores de implementaciones de ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mantiene los archivos de registro de activación para todas las implementaciones.  Estos registros documentan cualquier error relacionado con la instalación e inicialización de una implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  De forma predeterminada, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] crea un archivo de registro para cada activación de implementación.  Almacena estos archivos de registro en la carpeta Archivos temporales de Internet.  El archivo de registro para una implementación se muestra al usuario cuando se produce un error de activación y el usuario hace clic en **Detalles** en el cuadro de diálogo de error que aparece.  
  
 Puede cambiar este comportamiento para un cliente concreto mediante el Editor del Registro \(**regedit.exe**\) para establecer una ruta de acceso del archivo de registro personalizada.  En este caso, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] graba las activaciones correctas y los errores de todas las implementaciones en un archivo único.  
  
> [!CAUTION]
>  El uso incorrecto del Editor del Registro puede causar problemas graves que obliguen a reinstalar el sistema operativo.  Utilice el Editor del registro bajo su propia responsabilidad.  
  
> [!NOTE]
>  Necesitará truncar o eliminar de vez en cuando el archivo de registro para evitar que crezca demasiado.  
  
 El procedimiento siguiente describe cómo establecer una ubicación del archivo de registro personalizada para un cliente único.  
  
### Para establecer una ubicación del archivo de registro personalizada  
  
1.  Abra **Regedit.exe**.  
  
2.  Navegue hasta el nodo `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Establezca el valor de cadena `LogFilePath` en la ruta de acceso completa y el nombre de archivo de la ubicación de registro personalizada que prefiera.  
  
     Esta ubicación debe estar en un directorio en el que el usuario tenga acceso de escritura.  Por ejemplo, en Windows Vista, cree la siguiente estructura de carpetas y establezca `LogFilePath` en C:\\Usuarios\\\<nombreDeUsuario\>\\Documentos\\Logs\\ClickOnce\\installation.log.  
  
## Vea también  
 [Solucionar problemas en implementaciones ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)