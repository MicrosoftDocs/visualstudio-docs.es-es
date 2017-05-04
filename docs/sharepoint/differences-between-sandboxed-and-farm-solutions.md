---
title: "Diferencias entre soluciones en espacio aislado y soluciones de granja | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "soluciones de granja de servidores [desarrollo de SharePoint en Visual Studio]"
  - "soluciones en espacio aislado [desarrollo de SharePoint en Visual Studio]"
  - "desarrollo de SharePoint en Visual Studio, soluciones de granja de servidores"
  - "desarrollo de SharePoint en Visual Studio, soluciones en espacio aislado"
ms.assetid: 43beb7e7-0cd9-4a8f-bb72-6b1e0cba5be8
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Diferencias entre soluciones en espacio aislado y soluciones de granja
  Al compilar una solución de SharePoint, se implementa en el servidor de SharePoint y se adjunta un depurador para depurarla.  El proceso utilizado para depurar la solución depende del valor de la propiedad Solución en espacio aislado o solución de granja de servidores.  
  
 Para obtener más información, vea [Consideraciones sobre las soluciones en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).  
  
## Soluciones de granja de servidores  
 Las soluciones de granja de servidores que se hospedan en el proceso de trabajo IIS \(W3WP.exe\) ejecutan código que puede afectar a la granja entera.  Cuando depura un proyecto de SharePoint cuya propiedad Solución en espacio aislado está establecida en "solución de granja de servidores", el grupo de aplicaciones IIS del sistema se recicla antes de que SharePoint retraiga o implemente la característica para liberar cualquier archivo bloqueado por el proceso de trabajo IIS.  Solo se recicla el grupo de aplicaciones IIS que sirve a la dirección URL del sitio del proyecto SharePoint.  
  
## Soluciones en espacio aislado  
 Las soluciones en espacio aislado, que se hospedan en el proceso de trabajo de solución de código de usuario de SharePoint \(SPUCWorkerProcess.exe\), ejecutan código que solo puede afectar a la colección de sitios de la solución.  Dado que las soluciones en espacio aislado no se ejecutan en el proceso de trabajo IIS, ni el grupo de aplicaciones IIS ni el servidor IIS se deben reiniciar.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] adjunta el depurador al proceso SPUCWorkerProcess que el servicio SPUserCodeV4 en SharePoint activa y controla automáticamente.  No es necesario que SPUCWorkerProcess se recicle para cargar la versión última de la solución.  
  
## Todo tipo de solución  
 Con cualquier tipo de solución, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] adjunta también el depurador al explorador para habilitar la depuración de script de cliente.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utiliza el motor de depuración de script para este propósito.  Para habilitar la depuración de script, debe cambiar los valores predeterminados de explorador cuando se le pida.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] solo adjunta el depurador a los procesos de W3WP o SPUCWorkerProcess que se ejecutan en el sitio actual.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] también adjunta los motores de depuración del flujo de trabajo y COM Plus administrado.  
  
## Vea también  
 [Depurar soluciones de SharePoint](../sharepoint/debugging-sharepoint-solutions.md)   
 [Compilar y depurar soluciones de SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Consideraciones sobre las soluciones en espacio aislado](../sharepoint/sandboxed-solution-considerations.md)  
  
  