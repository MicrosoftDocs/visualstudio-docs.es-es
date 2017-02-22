---
title: "C&#243;mo realiza ClickOnce actualizaciones de aplicaciones | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "implementación ClickOnce, actualizaciones"
  - "implementar aplicaciones [ClickOnce], actualizaciones de aplicaciones"
  - "actualizaciones, ClickOnce"
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# C&#243;mo realiza ClickOnce actualizaciones de aplicaciones
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ClickOnce utiliza la información de la versión del archivo especificada en el manifiesto de implementación de una aplicación para decidir si debe actualizar los archivos de la aplicación.  Una vez que se inicia una actualización, ClickOnce utiliza una técnica denominada *revisión de archivos* para evitar que se produzca una descarga redundante de archivos de aplicación.  
  
## Revisión de archivos  
 Al actualizar una aplicación, ClickOnce no descarga todos los archivos para la nueva versión de la aplicación, a menos que los archivos hayan cambiado.  En lugar de ello, compara las firmas hash de los archivos especificados en el manifiesto de aplicación de la aplicación actual con las firmas del manifiesto de la nueva versión.  Si las firmas de un archivo son distintas, ClickOnce descarga la nueva versión.  Si las firmas coinciden, significa que el archivo no ha cambiado de una versión a la siguiente.  En este caso, ClickOnce copia el archivo existente y lo utiliza en la nueva versión de la aplicación.  Este método evita que ClickOnce tenga que descargar de nuevo la aplicación completa, aunque sólo hayan cambiado uno o dos archivos.  
  
 La revisión de archivos también funciona con los ensamblados que se descargan a petición mediante los métodos <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> y <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A>.  
  
 Si utiliza Visual Studio para compilar la aplicación, cada vez que recompile el proyecto completo se generarán nuevas firmas hash para todos los archivos.  En este caso, todos los ensamblados se descargarán en el cliente, aunque sólo hayan cambiado algunos de ellos.  
  
 La revisión de archivos no funciona con archivos marcados como datos y almacenados en el directorio de datos.  Estos archivos siempre se descargan, independientemente de la firma hash del archivo.  Para obtener más información sobre el directorio de datos, vea [Obtener acceso local o remoto a los datos en aplicaciones ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
## Vea también  
 [Elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Elegir una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)