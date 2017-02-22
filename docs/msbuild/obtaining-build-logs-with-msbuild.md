---
title: "Obtener registros de compilaci&#243;n con MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, registro"
  - "inicio de sesión [MSBuild]"
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
caps.latest.revision: 27
caps.handback.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Obtener registros de compilaci&#243;n con MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilizando los modificadores con MSBuild, puede especificar cuánto compilan datos que desea revisar y si desea guardar datos de compilación a uno o más archivos.  También puede especificar un registrador personalizado para recopilar datos de compilación.  Para obtener información sobre los modificadores de la línea de comandos de MSBuild que este tema no abarca, vea [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
>  Si compila proyectos mediante el IDE de Visual Studio, puede solucionar estas compilaciones revisando los registros compilados.  Para obtener más información, vea [Cómo: Ver, guardar y configurar archivos de registro de compilación](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
## Establecer el nivel de detalle  
 Cuando se compila un proyecto utilizando MSBuild sin especificar un nivel de detalle, la siguiente información aparece en la salida registrar:  
  
-   Errores, advertencias, y mensajes que se clasifican como muy importantes.  
  
-   Algunos eventos de estado.  
  
-   Un resumen de la compilación.  
  
 Utilizando el modificador **\/verbosity** \(**\/v**\), puede controlar la cantidad de datos aparece en el registro de salida.  Para solucionar problemas, utilice un nivel de detalle de `detailed` \(`d`\) o de `diagnostic` \(`diag`\), que proporciona la mayoría de la información.  
  
 El proceso de compilación puede ser más lento cuando se establece **\/verbosity** a `detailed` e incluso más lento cuando se establece **\/verbosity** a `diagnostic`.  
  
```  
msbuild MyProject.proj /t:go /v:diag  
```  
  
## Guardar la compilación registrar un archivo  
 Puede utilizar el modificador **\/fileLogger** \(**fl**\) para guardar datos de compilación en un archivo.  El ejemplo siguiente guarda datos de compilación a un archivo que se denomina `msbuild.log`.  
  
```  
msbuild MyProject.proj /t:go /fileLogger  
```  
  
 En el ejemplo siguiente, el archivo de registro se denomina `MyProjectOutput.log`, y el nivel de detalle del registro se establece en `diagnostic`.  Especifica esos dos valores utilizando el modificador **\/filelogparameters** \(`flp`\).  
  
```  
msbuild MyProject.proj /t:go /fl /flp:logfile=MyProjectOutput.log;verbosity=diagnostic  
```  
  
 Para obtener más información, vea [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md).  
  
## Guardar el registro generado en varios archivos  
 El ejemplo siguiente se guarda el registro completo a `msbuild1.log`, solo los errores a `JustErrors.log`, y simplemente las advertencias a `JustWarnings.log`.  El ejemplo utiliza números de archivo para cada uno de los tres archivos.  Números de archivo se especifican justo después de los modificadores de **\/fl** y de **\/flp** \(por ejemplo, `/fl1` y `/flp1`\).  
  
 Los modificadores de **\/filelogparameters** \(`flp`\) para archivos 2 y 3 especifican qué llamar a cada archivo y qué incluir en cada archivo.  No se especifica ningún nombre para el archivo 1, por lo que el nombre predeterminado de `msbuild1.log` se utiliza.  
  
```  
msbuild MyProject.proj /t:go /fl1 /fl2 /fl3 /flp2:logfile=JustErrors.log;errorsonly /flp3:logfile=JustWarnings.log;warningsonly  
  
```  
  
 Para obtener más información, vea [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md).  
  
## Mediante un registrador personalizado  
 Puede escribir su propio registrador creando un tipo administrado que implemente la interfaz <xref:Microsoft.Build.Framework.ILogger>.  Puede usar un registrador personalizado, por ejemplo, para enviar errores de compilación por correo electrónico, los registrar una base de datos, o los registrar un archivo XML.  Para obtener más información, vea [Registradores de compilación](../msbuild/build-loggers.md).  
  
 En la línea de comandos de MSBuild, especifique el registrador personalizado utilizando el modificador **\/logger**.  También puede utilizar el modificador **\/noconsolelogger** para deshabilitar el registrador de la consola predeterminado.  
  
## Vea también  
 <xref:Microsoft.Build.Framework.LoggerVerbosity>   
 [Registradores de compilación](../msbuild/build-loggers.md)   
 [Registrar en un entorno de varios procesadores](../msbuild/logging-in-a-multi-processor-environment.md)   
 [Crear registradores de reenvío](../msbuild/creating-forwarding-loggers.md)   
 [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)