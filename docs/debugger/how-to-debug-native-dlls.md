---
title: "C&#243;mo: Depurar DLL nativas | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.dll"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurar las DLL"
  - "DLL, depurar"
  - "archivos ejecutables, especificar para sesiones de depuración"
ms.assetid: 76b34d15-a66d-4963-842e-c8b955c81696
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Depurar DLL nativas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar su configuración, elija la opción Importar y exportar configuraciones del menú Herramientas.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Cuando se depura un archivo DLL, se puede iniciar la depuración desde:  
  
-   El proyecto utilizado para crear el archivo ejecutable que llama al archivo DLL.  
  
 O bien  
  
-   El proyecto utilizado para crear el propio archivo DLL.  
  
 Si tiene el proyecto utilizado para crear el archivo ejecutable, inicie la depuración desde ese proyecto.  Puede abrir entonces un archivo de código fuente para el archivo DLL y establecer puntos de interrupción en ese archivo, aunque no forme parte del proyecto utilizado para crear el archivo ejecutable.  Para obtener más información, vea [Puntos de interrupción](http://msdn.microsoft.com/es-es/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
 Si está depurando desde el proyecto que crea el archivo DLL, debe especificar el archivo ejecutable que desea utilizar en la depuración del archivo DLL.  
  
### Para especificar un archivo ejecutable para la sesión de depuración  
  
1.  En el **Explorador de soluciones**, seleccione el proyecto que crea el archivo DLL.  
  
2.  En el menú **Ver**, elija **Páginas de propiedades**.  
  
3.  En el cuadro de diálogo **Páginas de propiedades**, abra la carpeta **Propiedades de configuración** y seleccione la categoría **Depuración**.  
  
4.  En el cuadro **Comando**, especifique el nombre de la ruta de acceso del contenedor.  Por ejemplo, C:\\Archivos de programa\\MiAplicación\\MIAPLIC.EXE.  
  
5.  En el cuadro **Argumentos del comando**, especifique cualquier argumento necesario para el archivo ejecutable.  
  
 Si no especifica el archivo ejecutable en el cuadro de diálogo **Páginas de propiedades** del *Project*, aparecerá el cuadro de diálogo [Archivo ejecutable para sesión de depuración](../debugger/executable-for-debugging-session-dialog-box.md) al iniciar la depuración.  
  
## Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md)