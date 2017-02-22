---
title: "Distribuir aplicaciones de Shell aislado | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Distribuir aplicaciones de Shell aislado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Debe instalar Visual Studio y el SDK de Visual Studio para crear una aplicación de shell aislado. Para distribuir la aplicación a los equipos de otros usuarios o clientes, debe incluir un paquete redistribuible especial para el shell aislado.  
  
## Requisitos previos para la distribución de aplicaciones de Shell aislado  
  
|Nombre|Descripción|  
|------------|-----------------|  
|Visual Studio SDK|El SDK debe tener para desarrollar y probar las extensiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. También puede utilizar el SDK para crear su propia instancia del shell aislado de Visual Studio.<br /><br /> Visual Studio es un requisito previo para el SDK.|  
|Microsoft Visual Studio aislada Shell Redistributable|Incluir en el programa de instalación al crear un entorno de herramientas de Visual Studio redistribuible aislados de shell. El paquete redistribuible de Shell aislado incluye .NET Framework 4.5.|  
  
## Crear un programa de instalación para la aplicación  
 Debe crear un programa de instalación especial para la aplicación de shell aislado o integrada. Para obtener más información, consulta [Instalación de una aplicación de Shell aislado](../extensibility/installing-an-isolated-shell-application.md).  
  
## Permite actualizaciones en la aplicación  
 El programa de instalación debe permitir la posibilidad de que se actualizará la aplicación, las actualizaciones de Microsoft o las actualizaciones de su empresa. Para obtener más información acerca de las actualizaciones, consulte [El mantenimiento de las directrices de aplicaciones de Shell aislado](../extensibility/servicing-guidelines-for-isolated-shell-applications.md).