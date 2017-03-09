---
title: "Esta tarea requiere derechos adicionales | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.UACDialog"
ms.assetid: a03d3509-5e6e-411a-9aec-0766d7ee3a0e
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Esta tarea requiere derechos adicionales
Este error aparece si un usuario invoca un comando de Visual Studio cuya cuenta tiene permisos insuficientes para completar la operación.  
  
 Algunos comandos de Visual Studio deben ejecutarse con una cuenta que tenga permisos de acceso de usuario suficientes habilitar el comando de leer o escribir todos los archivos necesarios y claves del Registro.  Para obtener estos derechos, debe cerrar y abrir de nuevo Visual Studio con una cuenta que ha elevado el acceso, como un administrador.  
  
 Para obtener más información sobre permisos al ejecutar Visual Studio, vea [Permisos de usuario](../ide/user-permissions-and-visual-studio.md).  
  
### Para corregir este error  
  
1.  En el cuadro de diálogo, haga clic en **Reiniciar usando otra cuenta**.  
  
     Esto le solicita que guarde la solución actualmente cargada, y cierra Visual Studio y lo reinicia, solicitándole que utilice una cuenta diferente.  
  
2.  En el indicador de inicio de sesión, inicie sesión con una cuenta que tenga derechos más elevados que la cuenta anterior, como por ejemplo Administrador.  
  
     Cuando inicia Visual Studio, se realizan las recargas la última solución y la línea de comandos.  
  
> [!NOTE]
>  Iniciar sesión con una cuenta que tenga permisos superiores no garantiza necesariamente que el comando de Visual Studio.  Algunos comandos no se ejecuten correctamente incluso si utiliza una cuenta de Administrador.