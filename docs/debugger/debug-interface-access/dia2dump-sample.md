---
title: "Ejemplo Dia2dump | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aplicaciones de ejemplo [Kit de desarrollo DIA (SDK)]"
  - "Dia2dump (ejemplo) [Kit de desarrollo DIA (SDK)]"
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Ejemplo Dia2dump
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El ejemplo de Dia2dump se instala con Visual Studio y contiene el archivo de código fuente de Dia2dump.cpp.  El ejecutable compilado se ejecuta desde la línea de comandos y muestra el contenido de un archivo completo de la base de datos de programa \(.pdb\).  
  
### para instalar el ejemplo  
  
1.  Compruebe que el sistema cumple todos los requisitos de configuración descritos en la página de inicio de la configuración de Visual Studio.  
  
2.  Instale Visual Studio y siga todas las instrucciones de configuración e instalación para los ejemplos incluidos.  
  
#### Para compilar el ejemplo  
  
1.  Abra el archivo de Dia2dump.sln en Visual Studio.  \(En caso necesario, Visual Studio le ayudará a actualizar el proyecto de Dia2dump.\)  
  
2.  En las páginas de propiedades del proyecto, en **C\/C\+\+** &#124; **General** &#124; la propiedad de**Directorios de inclusión adicionales** , especifica el directorio de `. \DIA SDK \ include` .  esto garantiza que el compilador puede encontrar el archivo de dia2.h.  
  
3.  En el menú **Compilar**, haga clic en **Recompilar solución**.  
  
4.  Cierra Visual Studio.  
  
#### Para ejecutar el ejemplo  
  
1.  Abra un símbolo del sistema y escriba lo siguiente:  
  
    ```  
    dia2dump filename  
    ```  
  
## Vea también  
 [Archivo de origen Dia2dump.cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)   
 [Cómo: Solucionar problemas de actualizaciones de proyecto de Visual Studio incorrectas](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)