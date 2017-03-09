---
title: "No se pueden restaurar algunas asociaciones de archivo predeterminadas. Nota: Debe ser administrador o usuario avanzado de esta m&#225;quina para poder cambiar las asociaciones de archivo. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.Message.0x00006A85"
  - "VS_E_RESTOREFILEASSOCS"
ms.assetid: 449c5608-83e3-4ddd-91f1-1061916995b3
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# No se pueden restaurar algunas asociaciones de archivo predeterminadas. Nota: Debe ser administrador o usuario avanzado de esta m&#225;quina para poder cambiar las asociaciones de archivo.
Este error se produce cuando se utiliza el modificador de la línea de comandos devenv \/AssociateFiles, pero los derechos del usuario actual no permiten el acceso a la sección HKEY\_CLASSES\_ROOT del registro. Al ejecutar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)], debe ejecutar devenv como administrador para utilizar el modificador\/AssociateFiles \(devenv.exe\).  
  
### Para corregir este error  
  
-   Cambie a las credenciales administrativas e inténtelo de nuevo.  
  
## Vea también  
 [User Rights and Visual Studio](http://msdn.microsoft.com/es-es/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Modificadores de línea de comandos para Devenv](../ide/reference/devenv-command-line-switches.md)