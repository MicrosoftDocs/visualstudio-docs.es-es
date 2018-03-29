---
title: Obtener registros de compilación con MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: msbuild
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, logging
- logging [MSBuild]
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
caps.latest.revision: ''
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ba20e37e9a984512e2d63de882d434b4f034120d
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2018
---
# <a name="obtaining-build-logs-with-msbuild"></a>Obtener registros de compilación con MSBuild
Mediante el uso de modificadores con MSBuild, puede especificar la cantidad de datos de compilación que quiere revisar y si quiere guardarlos en uno o más archivos. También puede especificar un registrador personalizado para recopilar datos de compilación. Para obtener información sobre los modificadores de la línea de comandos de MSBuild que no se tratan en este tema, consulte [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
>  Si compila proyectos mediante el IDE de Visual Studio, puede solucionar las compilaciones mediante la revisión de los registros de compilación. Para obtener más información, consulte [Cómo: Ver, guardar y configurar archivos de registro de compilación](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
## <a name="setting-the-level-of-detail"></a>Establecer el nivel de detalle  
 Cuando compila un proyecto mediante el uso de MSBuild sin especificar un nivel de detalle, la siguiente información aparece en el registro de salida:  
  
-   Errores, advertencias y mensajes que están clasificados como muy importantes.  
  
-   Algunos eventos de estado.  
  
-   Un resumen de la compilación.  
  
 Mediante el uso del modificador **verbosity** (**/v**), puede controlar la cantidad de datos que aparecen en el registro de salida. Para solucionar el problema, utilice un nivel de detalle del `detailed` (`d`) o `diagnostic` (`diag`), que proporciona más información.  
  
 El proceso de compilación puede ser más lento cuando **/verbosity** se establece en `detailed` e incluso más lento al establecer **/verbosity** en `diagnostic`.  
  
```  
msbuild MyProject.proj /t:go /v:diag  
```  

## <a name="saving-the-build-log-to-a-file"></a>Guardar el registro de compilación en un archivo  
 Puede usar el modificador **/fileLogger** (**fl**) para guardar los datos de compilación en un archivo. En el ejemplo siguiente, los datos de compilación se guardan en un archivo denominado `msbuild.log`.  
  
```  
msbuild MyProject.proj /t:go /fileLogger  
```  
  
 En el ejemplo siguiente, el archivo de registro se denomina `MyProjectOutput.log`, y el nivel de detalle de la salida del registro se establece en `diagnostic`. Puede especificar las dos configuraciones mediante el modificador **/filelogparameters** (`flp`).  
  
```  
msbuild MyProject.proj /t:go /fl /flp:logfile=MyProjectOutput.log;verbosity=diagnostic  
```  
  
 Para obtener más información, vea [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="saving-the-log-output-to-multiple-files"></a>Guardar la salida del registro en varios archivos  
 En el ejemplo siguiente se guarda el registro completo en `msbuild1.log`, solo los errores en `JustErrors.log` y solo las advertencias en `JustWarnings.log`. En el ejemplo se utilizan números de archivo para cada uno de los tres archivos. Los números de archivo se especifican justo después de los modificadores **/fl** y **/flp** (por ejemplo, `/fl1` y `/flp1`).  
  
 Los modificadores **/filelogparameters** (`flp`) para los archivos 2 y 3 especifican el nombre de cada archivo y qué se va a incluir en cada archivo. No se especifica ningún nombre para el archivo 1, por lo que se utiliza el nombre predeterminado de `msbuild1.log`.  
  
```  
msbuild MyProject.proj /t:go /fl1 /fl2 /fl3 /flp2:logfile=JustErrors.log;errorsonly /flp3:logfile=JustWarnings.log;warningsonly  
  
```  
  
 Para obtener más información, vea [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md).  

## <a name="saving-a-binary-log"></a>Guardar un registro binario

Puede guardar el registro en formato comprimido y binario con el modificador **/binaryLogger** (**bl**). Este registro incluye una descripción detallada del proceso de compilación y puede ser leído por determinadas herramientas de análisis de registro.

En el ejemplo siguiente, se crea un archivo de registro binario llamado `binarylogfilename`.

```  
/bl:binarylogfilename.binlog
``` 
 
Para obtener más información, vea [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md).  

## <a name="using-a-custom-logger"></a>Usar un registrador personalizado  
 Para escribir su propio registrador, cree un tipo administrado que implemente la interfaz <xref:Microsoft.Build.Framework.ILogger>. Puede usar un registrador personalizado, por ejemplo, para enviar errores de compilación por correo electrónico o para registrarlos en una base de datos o en un archivo XML. Para obtener más información, consulte [Registradores de compilación](../msbuild/build-loggers.md).  
  
 En la línea de comandos de MSBuild, especifique el registrador personalizado mediante el modificador **/logger**. También puede utilizar el modificador **/noconsolelogger** para desactivar el registrador de consola predeterminado.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.Build.Framework.LoggerVerbosity>   
 [Registradores de compilación](../msbuild/build-loggers.md)   
 [Registrar en un entorno de varios procesadores](../msbuild/logging-in-a-multi-processor-environment.md)   
 [Crear registradores de reenvío](../msbuild/creating-forwarding-loggers.md)   
 [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)